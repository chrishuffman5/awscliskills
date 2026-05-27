# AWS CLI v2 -- Private CA (acm-pca) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/acm-pca/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-certificate-authority` | CA | Create a private certificate authority |
| `delete-certificate-authority` | CA | Delete a certificate authority |
| `describe-certificate-authority` | CA | Get detailed information about a CA |
| `list-certificate-authorities` | CA | List all CAs in the account |
| `update-certificate-authority` | CA | Update CA configuration or status |
| `restore-certificate-authority` | CA | Restore a deleted CA (within retention period) |
| `get-certificate-authority-certificate` | CA | Get the CA's own certificate and chain |
| `get-certificate-authority-csr` | CA | Get the CSR for the CA |
| `import-certificate-authority-certificate` | CA | Import a signed certificate for the CA |
| `issue-certificate` | Certificate | Issue a new certificate from a CA |
| `get-certificate` | Certificate | Retrieve an issued certificate |
| `revoke-certificate` | Certificate | Revoke an issued certificate |
| `create-certificate-authority-audit-report` | Audit | Generate an audit report for a CA |
| `describe-certificate-authority-audit-report` | Audit | Get details about a CA audit report |
| `create-permission` | Permission | Grant permissions on a CA to an AWS service |
| `delete-permission` | Permission | Revoke permissions from a CA |
| `list-permissions` | Permission | List permissions for a CA |
| `get-policy` | Policy | Retrieve the resource policy for a CA |
| `put-policy` | Policy | Attach a resource policy to a CA |
| `delete-policy` | Policy | Delete the resource policy from a CA |
| `tag-certificate-authority` | Tag | Add tags to a CA |
| `untag-certificate-authority` | Tag | Remove tags from a CA |
| `list-tags` | Tag | List tags for a CA |
| `wait` | Wait | Wait for CA operations to complete |

---

## Global Options

These options are available on ALL `aws acm-pca` commands.

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

### CA Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | CA is being created |
| `PENDING_CERTIFICATE` | CA has been created but needs a certificate installed |
| `ACTIVE` | CA is active and can issue certificates |
| `DISABLED` | CA is disabled and cannot issue certificates |
| `EXPIRED` | CA certificate has expired |
| `FAILED` | CA creation failed |
| `DELETED` | CA has been deleted (restorable within retention period) |

### CA Types
| Type | Description |
|------|-------------|
| `ROOT` | Self-signed root CA |
| `SUBORDINATE` | CA signed by a parent CA |

### Key Algorithms
| Algorithm | Description |
|-----------|-------------|
| `RSA_2048` | RSA 2048-bit key |
| `RSA_3072` | RSA 3072-bit key |
| `RSA_4096` | RSA 4096-bit key |
| `EC_prime256v1` | ECDSA P-256 key |
| `EC_secp384r1` | ECDSA P-384 key |
| `EC_secp521r1` | ECDSA P-521 key |

### Signing Algorithms
| Algorithm | Description |
|-----------|-------------|
| `SHA256WITHRSA` | SHA-256 with RSA |
| `SHA384WITHRSA` | SHA-384 with RSA |
| `SHA512WITHRSA` | SHA-512 with RSA |
| `SHA256WITHECDSA` | SHA-256 with ECDSA |
| `SHA384WITHECDSA` | SHA-384 with ECDSA |
| `SHA512WITHECDSA` | SHA-512 with ECDSA |

### Revocation Reasons
| Reason | Description |
|--------|-------------|
| `UNSPECIFIED` | No specific reason |
| `KEY_COMPROMISE` | Private key was compromised |
| `CERTIFICATE_AUTHORITY_COMPROMISE` | CA was compromised |
| `AFFILIATION_CHANGED` | Subject affiliation changed |
| `SUPERSEDED` | Certificate has been replaced |
| `CESSATION_OF_OPERATION` | Subject has ceased operations |
| `PRIVILEGE_WITHDRAWN` | Privileges were withdrawn |
| `A_A_COMPROMISE` | Attribute authority was compromised |

### Usage Modes
| Mode | Description |
|------|-------------|
| `GENERAL_PURPOSE` | Standard certificates with configurable validity |
| `SHORT_LIVED_CERTIFICATE` | Certificates with maximum 7-day validity, no revocation |
