# AWS CLI v2 -- IAM Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/iam/

---


## All IAM Subcommands (Quick Reference)

| Command | Category | Description |
|---------|----------|-------------|
| `add-client-id-to-open-id-connect-provider` | OIDC | Add client ID to OIDC provider |
| `add-role-to-instance-profile` | Instance Profile | Add role to instance profile |
| `add-user-to-group` | Group | Add user to group |
| `attach-group-policy` | Policy Attachment | Attach managed policy to group |
| `attach-role-policy` | Policy Attachment | Attach managed policy to role |
| `attach-user-policy` | Policy Attachment | Attach managed policy to user |
| `change-password` | Login Profile | Change own password |
| `create-access-key` | Access Key | Create access key pair |
| `create-account-alias` | Account | Create account alias |
| `create-group` | Group | Create a group |
| `create-instance-profile` | Instance Profile | Create instance profile |
| `create-login-profile` | Login Profile | Create console login password |
| `create-open-id-connect-provider` | OIDC | Create OIDC identity provider |
| `create-policy` | Managed Policy | Create managed policy |
| `create-policy-version` | Managed Policy | Create new policy version |
| `create-role` | Role | Create a role |
| `create-saml-provider` | SAML | Create SAML identity provider |
| `create-service-linked-role` | Service-Linked Role | Create service-linked role |
| `create-service-specific-credential` | Service Credential | Create service-specific credential |
| `create-user` | User | Create a user |
| `create-virtual-mfa-device` | MFA | Create virtual MFA device |
| `deactivate-mfa-device` | MFA | Deactivate MFA device |
| `delete-access-key` | Access Key | Delete access key |
| `delete-account-alias` | Account | Delete account alias |
| `delete-account-password-policy` | Account | Delete password policy |
| `delete-group` | Group | Delete a group |
| `delete-group-policy` | Inline Policy | Delete inline group policy |
| `delete-instance-profile` | Instance Profile | Delete instance profile |
| `delete-login-profile` | Login Profile | Delete console login password |
| `delete-open-id-connect-provider` | OIDC | Delete OIDC provider |
| `delete-policy` | Managed Policy | Delete managed policy |
| `delete-policy-version` | Managed Policy | Delete policy version |
| `delete-role` | Role | Delete a role |
| `delete-role-permissions-boundary` | Permissions Boundary | Remove role permissions boundary |
| `delete-role-policy` | Inline Policy | Delete inline role policy |
| `delete-saml-provider` | SAML | Delete SAML provider |
| `delete-server-certificate` | Server Certificate | Delete server certificate |
| `delete-service-linked-role` | Service-Linked Role | Delete service-linked role |
| `delete-service-specific-credential` | Service Credential | Delete service-specific credential |
| `delete-signing-certificate` | Signing Certificate | Delete signing certificate |
| `delete-ssh-public-key` | SSH Key | Delete SSH public key |
| `delete-user` | User | Delete a user |
| `delete-user-permissions-boundary` | Permissions Boundary | Remove user permissions boundary |
| `delete-user-policy` | Inline Policy | Delete inline user policy |
| `delete-virtual-mfa-device` | MFA | Delete virtual MFA device |
| `detach-group-policy` | Policy Attachment | Detach managed policy from group |
| `detach-role-policy` | Policy Attachment | Detach managed policy from role |
| `detach-user-policy` | Policy Attachment | Detach managed policy from user |
| `enable-mfa-device` | MFA | Enable MFA device for user |
| `generate-credential-report` | Reporting | Generate credential report |
| `generate-organizations-access-report` | Reporting | Generate Organizations access report |
| `generate-service-last-accessed-details` | Reporting | Generate service access details |
| `get-access-key-last-used` | Access Key | Get last usage info for access key |
| `get-account-authorization-details` | Account | Get all users, roles, groups, policies |
| `get-account-password-policy` | Account | Get password policy |
| `get-account-summary` | Account | Get account usage summary |
| `get-context-keys-for-custom-policy` | Simulation | Extract context keys from policy |
| `get-context-keys-for-principal-policy` | Simulation | Extract context keys for principal |
| `get-credential-report` | Reporting | Download credential report |
| `get-group` | Group | Get group details and members |
| `get-group-policy` | Inline Policy | Get inline group policy document |
| `get-instance-profile` | Instance Profile | Get instance profile details |
| `get-login-profile` | Login Profile | Get login profile details |
| `get-mfa-device` | MFA | Get MFA device details |
| `get-open-id-connect-provider` | OIDC | Get OIDC provider details |
| `get-organizations-access-report` | Reporting | Get Organizations access report |
| `get-policy` | Managed Policy | Get managed policy metadata |
| `get-policy-version` | Managed Policy | Get policy version document |
| `get-role` | Role | Get role details |
| `get-role-policy` | Inline Policy | Get inline role policy document |
| `get-saml-provider` | SAML | Get SAML provider details |
| `get-server-certificate` | Server Certificate | Get server certificate details |
| `get-service-last-accessed-details` | Reporting | Get service access details |
| `get-service-last-accessed-details-with-entities` | Reporting | Get access details with entities |
| `get-service-linked-role-deletion-status` | Service-Linked Role | Check deletion status |
| `get-ssh-public-key` | SSH Key | Get SSH public key |
| `get-user` | User | Get user details |
| `get-user-policy` | Inline Policy | Get inline user policy document |
| `list-access-keys` | Access Key | List access keys for user |
| `list-account-aliases` | Account | List account aliases |
| `list-attached-group-policies` | Policy Attachment | List policies attached to group |
| `list-attached-role-policies` | Policy Attachment | List policies attached to role |
| `list-attached-user-policies` | Policy Attachment | List policies attached to user |
| `list-entities-for-policy` | Policy Attachment | List entities using a policy |
| `list-group-policies` | Inline Policy | List inline group policy names |
| `list-groups` | Group | List all groups |
| `list-groups-for-user` | Group | List groups for a user |
| `list-instance-profile-tags` | Tags | List instance profile tags |
| `list-instance-profiles` | Instance Profile | List all instance profiles |
| `list-instance-profiles-for-role` | Instance Profile | List instance profiles for role |
| `list-mfa-device-tags` | Tags | List MFA device tags |
| `list-mfa-devices` | MFA | List MFA devices for user |
| `list-open-id-connect-provider-tags` | Tags | List OIDC provider tags |
| `list-open-id-connect-providers` | OIDC | List all OIDC providers |
| `list-policies` | Managed Policy | List managed policies |
| `list-policies-granting-service-access` | Reporting | List policies granting service access |
| `list-policy-tags` | Tags | List policy tags |
| `list-policy-versions` | Managed Policy | List policy versions |
| `list-role-policies` | Inline Policy | List inline role policy names |
| `list-role-tags` | Tags | List role tags |
| `list-roles` | Role | List all roles |
| `list-saml-provider-tags` | Tags | List SAML provider tags |
| `list-saml-providers` | SAML | List all SAML providers |
| `list-server-certificate-tags` | Tags | List server certificate tags |
| `list-server-certificates` | Server Certificate | List server certificates |
| `list-service-specific-credentials` | Service Credential | List service-specific credentials |
| `list-signing-certificates` | Signing Certificate | List signing certificates |
| `list-ssh-public-keys` | SSH Key | List SSH public keys |
| `list-user-policies` | Inline Policy | List inline user policy names |
| `list-user-tags` | Tags | List user tags |
| `list-users` | User | List all users |
| `list-virtual-mfa-devices` | MFA | List virtual MFA devices |
| `put-group-policy` | Inline Policy | Create/update inline group policy |
| `put-role-permissions-boundary` | Permissions Boundary | Set role permissions boundary |
| `put-role-policy` | Inline Policy | Create/update inline role policy |
| `put-user-permissions-boundary` | Permissions Boundary | Set user permissions boundary |
| `put-user-policy` | Inline Policy | Create/update inline user policy |
| `remove-client-id-from-open-id-connect-provider` | OIDC | Remove client ID from OIDC provider |
| `remove-role-from-instance-profile` | Instance Profile | Remove role from instance profile |
| `remove-user-from-group` | Group | Remove user from group |
| `reset-service-specific-credential` | Service Credential | Reset service-specific credential |
| `resync-mfa-device` | MFA | Resynchronize MFA device |
| `set-default-policy-version` | Managed Policy | Set default policy version |
| `set-security-token-service-preferences` | Account | Set STS global/regional endpoint |
| `simulate-custom-policy` | Simulation | Simulate effects of custom policy |
| `simulate-principal-policy` | Simulation | Simulate effects of principal's policies |
| `tag-instance-profile` | Tags | Tag instance profile |
| `tag-mfa-device` | Tags | Tag MFA device |
| `tag-open-id-connect-provider` | Tags | Tag OIDC provider |
| `tag-policy` | Tags | Tag managed policy |
| `tag-role` | Tags | Tag role |
| `tag-saml-provider` | Tags | Tag SAML provider |
| `tag-server-certificate` | Tags | Tag server certificate |
| `tag-user` | Tags | Tag user |
| `untag-instance-profile` | Tags | Remove tags from instance profile |
| `untag-mfa-device` | Tags | Remove tags from MFA device |
| `untag-open-id-connect-provider` | Tags | Remove tags from OIDC provider |
| `untag-policy` | Tags | Remove tags from managed policy |
| `untag-role` | Tags | Remove tags from role |
| `untag-saml-provider` | Tags | Remove tags from SAML provider |
| `untag-server-certificate` | Tags | Remove tags from server certificate |
| `untag-user` | Tags | Remove tags from user |
| `update-access-key` | Access Key | Activate/deactivate access key |
| `update-account-password-policy` | Account | Set password policy |
| `update-assume-role-policy` | Role | Update role trust policy |
| `update-group` | Group | Rename or re-path group |
| `update-login-profile` | Login Profile | Update console password |
| `update-open-id-connect-provider-thumbprint` | OIDC | Update OIDC thumbprint list |
| `update-role` | Role | Update role max session duration |
| `update-role-description` | Role | Update role description |
| `update-saml-provider` | SAML | Update SAML metadata document |
| `update-server-certificate` | Server Certificate | Rename or re-path server cert |
| `update-service-specific-credential` | Service Credential | Activate/deactivate credential |
| `update-signing-certificate` | Signing Certificate | Activate/deactivate signing cert |
| `update-ssh-public-key` | SSH Key | Activate/deactivate SSH key |
| `update-user` | User | Rename or re-path user |
| `upload-server-certificate` | Server Certificate | Upload server certificate |
| `upload-signing-certificate` | Signing Certificate | Upload signing certificate |
| `upload-ssh-public-key` | SSH Key | Upload SSH public key |

---


## Global Options Reference

These options are available on all `aws iam` commands:

| Option | Description |
|--------|-------------|
| `--debug` | Enable debug logging |
| `--endpoint-url <url>` | Override the default endpoint URL |
| `--no-verify-ssl` | Disable SSL certificate verification |
| `--no-paginate` | Disable automatic pagination |
| `--output <format>` | Output format: `json`, `yaml`, `yaml-stream`, `text`, `table` |
| `--query <jmespath>` | JMESPath query to filter output |
| `--profile <name>` | Named profile from config file |
| `--region <name>` | AWS region |
| `--version` | Display CLI version |
| `--color <on\|off\|auto>` | Turn on/off color output |
| `--no-sign-request` | Do not sign requests (anonymous) |
| `--ca-bundle <path>` | CA certificate bundle path |
| `--cli-read-timeout <seconds>` | Read timeout (default 60) |
| `--cli-connect-timeout <seconds>` | Connection timeout (default 60) |
| `--cli-binary-format <format>` | `base64` (default) or `raw-in-base64-out` |
| `--no-cli-pager` | Disable CLI pager |
| `--cli-auto-prompt` | Enable auto-prompt |
| `--no-cli-auto-prompt` | Disable auto-prompt |
