# Zero Trust Security with OCI — hands-on labs

Participant materials for **OUT1015 Zero Trust Security with OCI** at Oracle AI World 2026.

Summit Retail is moving its order system to Oracle Cloud Infrastructure (OCI). Asha, its cloud security lead, works through a series of security incidents. In the hands-on labs you fix three of them yourself.

| Lab | Incident | What you do |
|---|---|---|
| [Lab 0](lab0/README.md) | Set up your environment | Deploy the Summit Retail environment from Cloud Shell |
| Lab 1 | A password in the code | Move a database password into OCI Vault and read it with the instance's own identity |
| Lab 2 | A private app that isn't private | Use OCI Bastion, find an over-broad network rule, and remove it |
| Lab 3 | Attacks on an open web port | Inspect, block and rate-limit requests with OCI Web Application Firewall |

The activity guides are published on the workshop portal. This repository holds the Lab 0 package and its instructions.

## Quick start (Lab 0)

In the OCI Console of your lab account (region **US East (Ashburn)**), open **Cloud Shell** and run:

```bash
wget -O ~/OUT1015_Participant_Foundation_v6.zip https://github.com/SaurabhOCI/aiworld-2026-zero-trust-labs/raw/main/lab0/OUT1015_Participant_Foundation_v6.zip
unzip -n ~/OUT1015_Participant_Foundation_v6.zip -d ~/out1015-lab
cd ~/out1015-lab
python3 lab.py prepare
```

Then follow [Lab 0](lab0/README.md) to plan, deploy and check the environment.

## Clean up

After the workshop, follow the clean-up steps in [Lab 0](lab0/README.md#clean-up-after-the-workshop). The lab resources incur charges while they exist.
