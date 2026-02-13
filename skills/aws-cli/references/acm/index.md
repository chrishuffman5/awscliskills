# AWS CLI v2 -- ACM (AWS Certificate Manager) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/acm/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `request-certificate` | Certificate | Request a new ACM certificate |
| `describe-certificate` | Certificate | Get detailed info about a certificate |
| `delete-certificate` | Certificate | Delete a certificate |
| `list-certificates` | Certificate | List certificates in the account |
| `renew-certificate` | Certificate | Renew a private CA certificate |
| `resend-validation-email` | Certificate | Resend domain validation email |
| `import-certificate` | Import/Export | Import a third-party certificate |
| `export-certificate` | Import/Export | Export a private certificate with encrypted key |
| `get-certificate` | Import/Export | Retrieve certificate body and chain (no private key) |
| `add-tags-to-certificate` | Tags | Add tags to a certificate |
| `remove-tags-from-certificate` | Tags | Remove tags from a certificate |
| `list-tags-for-certificate` | Tags | List tags for a certificate |
| `get-account-configuration` | Account | Get account-level ACM configuration |
| `put-account-configuration` | Account | Set account-level ACM configuration |

---

## Global Options

These options are available on ALL `aws acm` commands.

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

### Certificate Status Values
| Status | Description |
|--------|-------------|
| `PENDING_VALIDATION` | Certificate is awaiting domain validation |
| `ISSUED` | Certificate has been issued and is valid |
| `INACTIVE` | Certificate has been revoked or otherwise made inactive |
| `REVOKED` | Certificate has been revoked |
| `EXPIRED` | Certificate has expired |
| `VALIDATION_TIMED_OUT` | Domain validation timed out |
| `FAILED` | Certificate request failed |

### Certificate Types
| Type | Description |
|------|-------------|
| `AMAZON_ISSUED` | Issued by ACM (public) |
| `PRIVATE` | Issued by ACM Private CA |
| `IMPORTED` | Imported third-party certificate |

### Key Algorithm Values
`RSA_1024`, `RSA_2048`, `RSA_3072`, `RSA_4096`, `EC_prime256v1`, `EC_secp384r1`, `EC_secp521r1`

### Validation Methods
- **DNS**: Create a CNAME record in your DNS configuration (recommended)
- **EMAIL**: Receive validation email at domain contact addresses

### Wait Commands
The `aws acm wait` subcommand blocks until a resource reaches a specific state:

| Waiter | Description |
|--------|-------------|
| `certificate-validated` | Wait until certificate status is ISSUED |

```bash
aws acm wait certificate-validated --certificate-arn arn:aws:acm:...
```
