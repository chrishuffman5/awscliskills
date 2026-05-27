# AWS CLI v2 -- Verified Permissions Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/verifiedpermissions/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-policy-store` | Policy Store | Create a new policy store |
| `delete-policy-store` | Policy Store | Delete a policy store |
| `get-policy-store` | Policy Store | Get details of a policy store |
| `list-policy-stores` | Policy Store | List all policy stores in the account |
| `update-policy-store` | Policy Store | Update policy store settings |
| `create-policy` | Policy | Create a Cedar policy (static or template-linked) |
| `delete-policy` | Policy | Delete a policy |
| `get-policy` | Policy | Get details of a policy |
| `list-policies` | Policy | List policies in a policy store |
| `update-policy` | Policy | Update an existing policy |
| `batch-get-policy` | Policy | Retrieve multiple policies in a single request |
| `create-policy-template` | Policy Template | Create a Cedar policy template |
| `delete-policy-template` | Policy Template | Delete a policy template |
| `get-policy-template` | Policy Template | Get details of a policy template |
| `list-policy-templates` | Policy Template | List policy templates in a policy store |
| `update-policy-template` | Policy Template | Update a policy template |
| `create-identity-source` | Identity Source | Create an identity source (Cognito/OIDC) |
| `delete-identity-source` | Identity Source | Delete an identity source |
| `get-identity-source` | Identity Source | Get details of an identity source |
| `list-identity-sources` | Identity Source | List identity sources in a policy store |
| `update-identity-source` | Identity Source | Update an identity source |
| `is-authorized` | Authorization | Check if a principal is authorized for an action |
| `is-authorized-with-token` | Authorization | Authorization check using identity tokens |
| `batch-is-authorized` | Authorization | Batch authorization checks (up to 30) |
| `batch-is-authorized-with-token` | Authorization | Batch authorization with identity tokens |
| `get-schema` | Schema | Retrieve the schema for a policy store |
| `put-schema` | Schema | Create or update a policy store schema |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws verifiedpermissions` commands.

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
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
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

### Policy Store ID
- **Pattern:** `[a-zA-Z0-9-/_]*`
- **Length:** 1-200 characters

### Policy Types
| Type | Description |
|------|-------------|
| `STATIC` | A standalone Cedar policy with inline principal/action/resource |
| `TEMPLATE_LINKED` | A policy instantiated from a policy template with slot values |

### Authorization Decisions
| Decision | Description |
|----------|-------------|
| `ALLOW` | The request is authorized by at least one permit policy |
| `DENY` | No permit policy matches, or an explicit forbid policy matches |

### Identity Source Types
| Type | Description |
|------|-------------|
| Cognito User Pool | Uses Amazon Cognito user pool tokens for authentication |
| OpenID Connect | Uses OIDC-compliant identity provider tokens |

### Validation Modes
| Mode | Description |
|------|-------------|
| `STRICT` | Validates all policies against the schema |
| `OFF` | No schema validation |

### Policy Effect Values
| Effect | Description |
|--------|-------------|
| `Permit` | Policy grants access |
| `Forbid` | Policy denies access |
