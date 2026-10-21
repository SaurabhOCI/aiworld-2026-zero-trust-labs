# Zero Trust Security with OCI — hands-on practices

Participant materials for **OUT1015 Zero Trust Security with OCI** at Oracle AI World 2026.

Summit Retail is moving its order system to Oracle Cloud Infrastructure (OCI). Asha, its cloud security lead, works through a series of security incidents. In the hands-on practices you fix three of them yourself.

| Practice | Incident | What you do |
|---|---|---|
| [Practice 0](lab0/README.md) | Set up your environment | Deploy the Summit Retail environment from Cloud Shell |
| Practice 1 | A password in the code | Move a database password into OCI Vault and read it with the instance's own identity |
| Practice 2 | A private app that isn't private | Use OCI Bastion, find an over-broad network rule, and remove it |
| Practice 3 | Attacks on an open web port | Inspect, block and rate-limit requests with OCI Web Application Firewall |

The activity guides are published on the workshop portal. PDF copies, one per practice:

| Practice | Guide |
|---|---|
| Practice 0: Prepare your environment | [OUT1015_Practice_0_Prepare_Environment_Activity_Guide.pdf](guides/OUT1015_Practice_0_Prepare_Environment_Activity_Guide.pdf) |
| Practice 1: OCI Vault secrets | [OUT1015_Practice_1_Vault_Secrets_Activity_Guide.pdf](guides/OUT1015_Practice_1_Vault_Secrets_Activity_Guide.pdf) |
| Practice 2: Security Lists, NSGs and Bastion | [OUT1015_Practice_2_VCN_Bastion_Activity_Guide.pdf](guides/OUT1015_Practice_2_VCN_Bastion_Activity_Guide.pdf) |
| Practice 3: Web Application Firewall | [OUT1015_Practice_3_WAF_Activity_Guide.pdf](guides/OUT1015_Practice_3_WAF_Activity_Guide.pdf) |

All four in one document: [OUT1015_Zero_Trust_Labs_Activity_Guide.pdf](guides/OUT1015_Zero_Trust_Labs_Activity_Guide.pdf). This repository also holds the Practice 0 package and its instructions.

## Quick start (Practice 0)

In the OCI Console of your lab account (region **US East (Ashburn)**), open **Cloud Shell** and run:

```bash
wget -O ~/OUT1015_Participant_Foundation_v6.zip https://github.com/SaurabhOCI/aiworld-2026-zero-trust-labs/raw/main/lab0/OUT1015_Participant_Foundation_v6.zip
unzip -n ~/OUT1015_Participant_Foundation_v6.zip -d ~/out1015-lab
cd ~/out1015-lab
python3 lab.py prepare
```

If GitHub is not reachable from Cloud Shell, use the Oracle Object Storage copy of the same file in the first command (link valid until 1 November 2026):

```text
https://objectstorage.us-ashburn-1.oraclecloud.com/p/7-3XsOEt1Q48HA2iREfVy1ZpHN94urCBIaySLK6lMScVxL36NTdpqJZ4hdCYCJc9/n/intoraclerohit/b/out1015-aiworld-2026-labs/o/lab0/OUT1015_Participant_Foundation_v6.zip
```

Then follow [Practice 0](lab0/README.md) to plan, deploy and check the environment.

## Clean up

After the workshop, follow the clean-up steps in [Practice 0](lab0/README.md#clean-up-after-the-workshop). The lab resources incur charges while they exist.

## After the workshop: self-paced practices

The instructor demonstrations can be repeated in your own OCI tenancy. See [self-paced/](self-paced/README.md) for the packages and activity guides.
