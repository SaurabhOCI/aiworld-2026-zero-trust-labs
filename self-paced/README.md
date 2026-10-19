# Self-paced labs: repeat the instructor demonstrations in your own tenancy

During OUT1015 you watched several incidents as instructor demonstrations. After the workshop you can repeat them in your own OCI tenancy. Each lab has a package, which builds the starting state from OCI Cloud Shell and removes it again, and an activity guide.

| Lab | Activity guide | Package | Time | Cost |
|---|---|---|---|---|
| Incident 1: IAM allow, deny and SSO | [Incident 1: Too Much Access](guides/OUT1015_SelfPaced_IAM_SSO_Activity_Guide.pdf) | `aiw-iam-sso-lab.zip` | about 1 hour | One small VM while the lab runs |
| ZPR: protect the business path | [Protect the Business Path with Zero Trust Packet Routing](guides/OUT1015_SelfPaced_ZPR_Activity_Guide.pdf) | `aiw-zpr-lab.zip` | about 1 hour 15 minutes | 3 small VMs and a load balancer while the lab runs |
| Incident 5: Data Safe masking | [Mask Customer Data in a Test Copy with Oracle Data Safe](guides/OUT1015_SelfPaced_DataSafe_Activity_Guide.pdf) | `aiw-datasafe-lab.zip` | about 75 minutes | Always Free database by default |
| AI agent tools: MCP and IAM application roles | [Control AI Agent Tools with OCI IAM Application Roles](guides/OUT1015_SelfPaced_MCP_Activity_Guide.pdf) | `aiw-mcp-lab.zip` | about 45 minutes | None (identity domain objects only) |

You need an OCI tenancy in which you are an administrator. Each guide lists its own prerequisites, and each package has a `teardown` command that removes everything it created.

All data in these labs is synthetic. The packages run in Cloud Shell with your own sign-in; they don't need or store API keys. Passwords and keys that a build creates stay in your Cloud Shell home directory.

