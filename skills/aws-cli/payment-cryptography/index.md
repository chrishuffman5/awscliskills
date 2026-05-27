# AWS CLI v2 — Payment Cryptography Command Reference Index

> Based on AWS CLI v2 documentation.
> Sources:
> - https://docs.aws.amazon.com/cli/latest/reference/payment-cryptography/
> - https://docs.aws.amazon.com/cli/latest/reference/payment-cryptography-data/

---

## Quick Reference

| Command | Namespace | Category | Description |
|---------|-----------|----------|-------------|
| `create-key` | payment-cryptography | Key | Create a new encryption key |
| `delete-key` | payment-cryptography | Key | Schedule key deletion |
| `get-key` | payment-cryptography | Key | Get key details |
| `list-keys` | payment-cryptography | Key | List all keys |
| `start-key-usage` | payment-cryptography | Key | Enable a key for use |
| `stop-key-usage` | payment-cryptography | Key | Disable a key |
| `restore-key` | payment-cryptography | Key | Cancel scheduled key deletion |
| `get-public-key-certificate` | payment-cryptography | Key | Get public key certificate (PEM) |
| `get-certificate-signing-request` | payment-cryptography | Key | Get a CSR for an asymmetric key |
| `import-key` | payment-cryptography | Import/Export | Import an encryption key |
| `export-key` | payment-cryptography | Import/Export | Export an encryption key |
| `get-parameters-for-import` | payment-cryptography | Import/Export | Get parameters for key import |
| `get-parameters-for-export` | payment-cryptography | Import/Export | Get parameters for key export |
| `create-alias` | payment-cryptography | Alias | Create a key alias |
| `delete-alias` | payment-cryptography | Alias | Delete a key alias |
| `get-alias` | payment-cryptography | Alias | Get alias details |
| `list-aliases` | payment-cryptography | Alias | List all aliases |
| `update-alias` | payment-cryptography | Alias | Update alias key association |
| `add-key-replication-regions` | payment-cryptography | Replication | Add replication regions to a key |
| `remove-key-replication-regions` | payment-cryptography | Replication | Remove replication regions from a key |
| `get-default-key-replication-regions` | payment-cryptography | Replication | Get account default replication regions |
| `enable-default-key-replication-regions` | payment-cryptography | Replication | Enable default replication regions |
| `disable-default-key-replication-regions` | payment-cryptography | Replication | Disable default replication regions |
| `tag-resource` | payment-cryptography | Tags | Add tags to a key |
| `untag-resource` | payment-cryptography | Tags | Remove tags from a key |
| `list-tags-for-resource` | payment-cryptography | Tags | List tags for a key |
| `encrypt-data` | payment-cryptography-data | Encryption | Encrypt payment data |
| `decrypt-data` | payment-cryptography-data | Encryption | Decrypt payment data |
| `re-encrypt-data` | payment-cryptography-data | Encryption | Re-encrypt data with a different key |
| `generate-pin-data` | payment-cryptography-data | PIN | Generate PIN data |
| `verify-pin-data` | payment-cryptography-data | PIN | Verify PIN data |
| `translate-pin-data` | payment-cryptography-data | PIN | Translate PIN block between formats/keys |
| `generate-mac-emv-pin-change` | payment-cryptography-data | PIN | Generate MAC for EMV PIN change |
| `generate-mac` | payment-cryptography-data | MAC | Generate message authentication code |
| `verify-mac` | payment-cryptography-data | MAC | Verify message authentication code |
| `generate-card-validation-data` | payment-cryptography-data | Card Validation | Generate CVV/CSC |
| `verify-card-validation-data` | payment-cryptography-data | Card Validation | Verify CVV/CSC |
| `verify-auth-request-cryptogram` | payment-cryptography-data | Card Validation | Verify ARQC and optionally generate ARPC |
| `generate-as2805-kek-validation` | payment-cryptography-data | Card Validation | Generate AS2805 KEK validation |
| `translate-key-material` | payment-cryptography-data | Card Validation | Translate key material between wrapping methods |

---

## Global Options

These options are available on ALL `aws payment-cryptography` and `aws payment-cryptography-data` commands.

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

### Key States
| State | Description |
|-------|-------------|
| `CREATE_IN_PROGRESS` | Key is being created |
| `CREATE_COMPLETE` | Key is ready for use |
| `DELETE_PENDING` | Key is scheduled for deletion |
| `DELETE_COMPLETE` | Key has been deleted |

### Key Origins
| Origin | Description |
|--------|-------------|
| `AWS_PAYMENT_CRYPTOGRAPHY` | Key created within the service |
| `EXTERNAL` | Key imported from outside |

### Key Algorithms
| Algorithm | Type | Description |
|-----------|------|-------------|
| `TDES_2KEY` | Symmetric | Triple DES with 2 keys |
| `TDES_3KEY` | Symmetric | Triple DES with 3 keys |
| `AES_128` | Symmetric | AES 128-bit |
| `AES_192` | Symmetric | AES 192-bit |
| `AES_256` | Symmetric | AES 256-bit |
| `RSA_2048` | Asymmetric | RSA 2048-bit |
| `RSA_3072` | Asymmetric | RSA 3072-bit |
| `RSA_4096` | Asymmetric | RSA 4096-bit |
| `ECC_NIST_P256` | Asymmetric | ECC NIST P-256 |
| `ECC_NIST_P384` | Asymmetric | ECC NIST P-384 |
| `ECC_NIST_P521` | Asymmetric | ECC NIST P-521 |
| `HMAC_SHA256` | Symmetric | HMAC with SHA-256 |
| `HMAC_SHA384` | Symmetric | HMAC with SHA-384 |
| `HMAC_SHA512` | Symmetric | HMAC with SHA-512 |

### Replication Statuses
| Status | Description |
|--------|-------------|
| `IN_PROGRESS` | Replication is in progress |
| `SYNCHRONIZED` | Key is synchronized across regions |
| `FAILED` | Replication failed |
| `DELETE_IN_PROGRESS` | Replica deletion in progress |
