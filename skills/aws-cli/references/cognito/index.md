# AWS CLI v2 -- Cognito Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/cognito-idp/ and https://docs.aws.amazon.com/cli/latest/reference/cognito-identity/

---

## Quick Reference -- `aws cognito-idp` (User Pools)

| Command | Category | Description |
|---------|----------|-------------|
| `create-user-pool` | User Pool | Create a new user pool |
| `delete-user-pool` | User Pool | Delete a user pool |
| `describe-user-pool` | User Pool | Get user pool details |
| `list-user-pools` | User Pool | List user pools |
| `update-user-pool` | User Pool | Update user pool configuration |
| `create-user-pool-client` | Client | Create a user pool app client |
| `delete-user-pool-client` | Client | Delete a user pool client |
| `describe-user-pool-client` | Client | Get client details |
| `list-user-pool-clients` | Client | List clients for a user pool |
| `update-user-pool-client` | Client | Update client configuration |
| `admin-create-user` | User | Create a user (admin) |
| `admin-delete-user` | User | Delete a user (admin) |
| `admin-get-user` | User | Get user details (admin) |
| `admin-set-user-password` | User | Set user password (admin) |
| `admin-confirm-sign-up` | User | Confirm user sign-up (admin) |
| `admin-disable-user` | User | Disable a user (admin) |
| `admin-enable-user` | User | Enable a user (admin) |
| `admin-update-user-attributes` | User | Update user attributes (admin) |
| `list-users` | User | List users in a user pool |
| `sign-up` | User | Register a new user (client-side) |
| `confirm-sign-up` | User | Confirm registration (client-side) |
| `forgot-password` | User | Initiate forgot password flow |
| `confirm-forgot-password` | User | Confirm new password |
| `create-group` | Group | Create a group |
| `delete-group` | Group | Delete a group |
| `get-group` | Group | Get group details |
| `list-groups` | Group | List groups in a user pool |
| `update-group` | Group | Update a group |
| `admin-add-user-to-group` | Group | Add a user to a group |
| `admin-remove-user-from-group` | Group | Remove a user from a group |
| `admin-list-groups-for-user` | Group | List groups for a user |
| `list-users-in-group` | Group | List users in a group |
| `create-identity-provider` | IdP | Create an identity provider |
| `delete-identity-provider` | IdP | Delete an identity provider |
| `describe-identity-provider` | IdP | Get identity provider details |
| `list-identity-providers` | IdP | List identity providers |
| `update-identity-provider` | IdP | Update an identity provider |
| `set-user-pool-mfa-config` | MFA | Set MFA configuration for user pool |
| `get-user-pool-mfa-config` | MFA | Get MFA configuration |
| `admin-set-user-mfa-preference` | MFA | Set MFA preference for a user (admin) |
| `set-user-mfa-preference` | MFA | Set MFA preference (authenticated user) |
| `associate-software-token` | MFA | Associate TOTP software token |
| `verify-software-token` | MFA | Verify TOTP software token |
| `create-user-pool-domain` | Domain | Create a custom domain |
| `delete-user-pool-domain` | Domain | Delete a custom domain |
| `describe-user-pool-domain` | Domain | Get domain details |
| `update-user-pool-domain` | Domain | Update a custom domain |
| `create-resource-server` | Resource Server | Create a resource server |
| `delete-resource-server` | Resource Server | Delete a resource server |
| `describe-resource-server` | Resource Server | Get resource server details |
| `list-resource-servers` | Resource Server | List resource servers |
| `update-resource-server` | Resource Server | Update a resource server |
| `admin-initiate-auth` | Auth | Initiate auth flow (admin) |
| `admin-respond-to-auth-challenge` | Auth | Respond to auth challenge (admin) |
| `initiate-auth` | Auth | Initiate auth flow (client-side) |
| `respond-to-auth-challenge` | Auth | Respond to auth challenge (client-side) |
| `admin-user-global-sign-out` | Auth | Sign out user from all devices (admin) |
| `global-sign-out` | Auth | Sign out from all devices (authenticated) |
| `revoke-token` | Auth | Revoke a refresh token |
| `tag-resource` | Tags | Add tags to a user pool |
| `untag-resource` | Tags | Remove tags from a user pool |
| `list-tags-for-resource` | Tags | List tags for a user pool |

## Quick Reference -- `aws cognito-identity` (Identity Pools)

| Command | Category | Description |
|---------|----------|-------------|
| `create-identity-pool` | Identity Pool | Create an identity pool |
| `delete-identity-pool` | Identity Pool | Delete an identity pool |
| `describe-identity-pool` | Identity Pool | Get identity pool details |
| `list-identity-pools` | Identity Pool | List identity pools |
| `update-identity-pool` | Identity Pool | Update an identity pool |
| `get-id` | Identity | Get or create an identity ID |
| `get-credentials-for-identity` | Identity | Get temporary AWS credentials |
| `get-open-id-token-for-developer-identity` | Identity | Get OpenID token for developer identity |
| `set-identity-pool-roles` | Roles | Set IAM roles for an identity pool |
| `get-identity-pool-roles` | Roles | Get IAM roles for an identity pool |
| `describe-identity` | Identity | Describe an identity |
| `list-identities` | Identity | List identities in a pool |
| `delete-identities` | Identity | Delete identities |
| `tag-resource` | Tags | Tag a resource |
| `untag-resource` | Tags | Untag a resource |
| `list-tags-for-resource` | Tags | List tags |

---

## Global Options

These options are available on ALL `aws cognito-idp` and `aws cognito-identity` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Auth Flow Types
| Flow | Description |
|------|-------------|
| `USER_PASSWORD_AUTH` | Username + password (client-side) |
| `USER_SRP_AUTH` | SRP-based authentication (client-side) |
| `ADMIN_USER_PASSWORD_AUTH` | Username + password (server-side/admin) |
| `ADMIN_NO_SRP_AUTH` | Admin auth without SRP |
| `CUSTOM_AUTH` | Custom authentication with Lambda triggers |
| `REFRESH_TOKEN_AUTH` | Refresh token exchange |
| `REFRESH_TOKEN` | Alias for REFRESH_TOKEN_AUTH |

### MFA Configuration Values
| Value | Description |
|-------|-------------|
| `OFF` | MFA disabled |
| `ON` | MFA required for all users |
| `OPTIONAL` | MFA optional per user |

### User Status Values
| Status | Description |
|--------|-------------|
| `UNCONFIRMED` | User registered but not confirmed |
| `CONFIRMED` | User confirmed |
| `ARCHIVED` | User archived/disabled |
| `COMPROMISED` | User marked as compromised |
| `UNKNOWN` | Unknown status |
| `RESET_REQUIRED` | Password reset required |
| `FORCE_CHANGE_PASSWORD` | User must change temporary password |

### Identity Provider Types
| Type | Description |
|------|-------------|
| `SAML` | SAML 2.0 provider |
| `Facebook` | Facebook Login |
| `Google` | Google Sign-In |
| `LoginWithAmazon` | Login with Amazon |
| `SignInWithApple` | Sign in with Apple |
| `OIDC` | Generic OpenID Connect provider |
