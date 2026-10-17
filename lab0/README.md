# OUT1015 Zero Trust Security with OCI — Lab 0 setup package

This package builds the Summit Retail environment that the hands-on labs use. You run it once, in your own Cloud Shell, at the start of the workshop. It takes about 20 minutes, most of it waiting for the servers to finish setting up.

## What it creates in your compartment

| Resource | Used in |
|---|---|
| Core VCN (10.42.0.0/16) with a public and a private subnet, internet, NAT and service gateways | Labs 1 and 2 |
| Tools VM in the public subnet, with the OCI CLI and Python SDK installed | Labs 1 and 2 |
| Order application VM in the private subnet, with no public IP address | Lab 2 |
| Public load balancer that sends customer traffic to the order application | Lab 2 |
| OCI Bastion for SSH sessions to the private VM | Lab 2 |
| Separate VCN (10.44.0.0/16) with a catalogue web server and its own public load balancer | Lab 3 |

That is 48 resources in total: 3 VMs (Arm A1, 1 OCPU and 6 GB each), 2 load balancers (10 Mbps) and 2 VCNs. Every name starts with `out1015-userNN`, where `userNN` is your participant number. The package creates no IAM policies, vaults, keys, secrets or WAF objects; you create the security controls yourself in the labs.

## Before you start

- Sign in to the OCI Console with the lab account your instructor gave you.
- Check that the region is **US East (Ashburn)**.
- Know the name of your assigned compartment, for example `98507690-C07`.

## Deploy

1. In the Console header, open **Developer tools** > **Cloud Shell**.
2. Download the package:

   ```bash
   wget -O ~/OUT1015_Participant_Foundation_v6.zip https://github.com/SaurabhOCI/aiworld-2026-zero-trust-labs/raw/main/lab0/OUT1015_Participant_Foundation_v6.zip
   ```

   If the download fails, use the Object Storage link in your activity guide, or upload the zip through the Cloud Shell menu (**Upload**).
3. Extract it once, then prepare:

   ```bash
   unzip -n ~/OUT1015_Participant_Foundation_v6.zip -d ~/out1015-lab
   cd ~/out1015-lab
   python3 lab.py prepare
   ```

   `prepare` shows your user name and proposes your participant number and compartment. Press **Enter** to accept each value, and **Enter** again to accept availability domain 1. If a proposed value is wrong, type the correct one.

4. Review the plan:

   ```bash
   python3 lab.py plan
   ```

   Expected last line: `Reviewed plan scope: {"create": 48, "update": 0, "delete": 0}`. Ignore Terraform's own suggestion to run `terraform apply`; use the next step instead.

5. Create the resources, and wait for the command to finish (about 5 minutes):

   ```bash
   python3 lab.py apply
   ```

6. Check the environment. The servers finish installing software after they start, and the private VM's Bastion plugin can take up to 15 minutes after `apply`. Rerun this command every minute until it ends with `Environment ready.`:

   ```bash
   python3 lab.py status
   ```

   Expected (your addresses differ):

   ```text
   Your Summit Retail environment (all values are saved in .local/outputs.json):
     tools_public_ip  150.136.72.83
     app_private_ip   10.42.1.207
     order_url        http://129.80.254.190
     catalogue_url    http://157.151.217.8
   Orders: HTTP 200; expected body matched: True
   Catalogue: HTTP 200; expected body matched: True
   Bastion plugin on the order application VM: RUNNING
   Environment ready.
   ```

7. Note the four values at the top. You use them in the labs.

Keep the `~/out1015-lab` folder for the whole workshop. Your SSH private key is `~/out1015-lab/.local/workshop_ssh`. It stays in Cloud Shell; do not share it.

To connect to the Tools VM:

```bash
ssh -i ~/out1015-lab/.local/workshop_ssh opc@<tools_public_ip>
```

## Rules the package follows

- It uses your Cloud Shell sign-in. It never asks for or stores passwords or API keys.
- It creates resources only in your compartment, and refuses a plan that would change anything else.
- It refuses to modify or replace existing resources. If a lab asks you to change a rule, change it by hand; do not run `apply` again to undo it.

## Troubleshooting

| Message | What to do |
|---|---|
| `Expected exactly one active compartment named ...` | Check the compartment name in your lab details and run `python3 lab.py prepare --compartment <name>`. |
| `Inputs already exist` | You already ran `prepare` in this folder. Continue with `plan`. |
| Limit, quota or capacity error during `apply` | Do not retry in another folder. Tell your instructor and keep the folder as it is. |
| `status` ends with `Not ready yet` | The servers are still starting. Wait a minute and run `status` again; it can take up to 15 minutes after `apply`. |
| `REMOTE HOST IDENTIFICATION HAS CHANGED` when you use SSH | You rebuilt the lab and Cloud Shell remembers the old VM. Run `ssh-keygen -R <address>` and connect again. |

## Clean up after the workshop

1. Delete anything you created by hand in the labs: WAF firewall and policy, logs and log group, Bastion sessions, and any temporary security rules. Schedule deletion of your key and secret in the vault.
2. Remove the Lab 0 resources:

   ```bash
   cd ~/out1015-lab
   python3 lab.py destroy-plan
   python3 lab.py destroy
   ```

   Type your prefix (for example `out1015-user07`) when asked. The command deletes only the resources this package created.
