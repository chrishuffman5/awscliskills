# AWS CLI v2 -- KMS (Key Management Service) Complete Command Reference

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/kms/

---

## All KMS Subcommands (Quick Reference)

| Command | Category | Description |
|---------|----------|-------------|
| `cancel-key-deletion` | Keys | Cancel scheduled key deletion |
| `connect-custom-key-store` | Custom Key Stores | Connect a custom key store |
| `create-alias` | Aliases | Create an alias for a key |
| `create-custom-key-store` | Custom Key Stores | Create a custom key store |
| `create-grant` | Grants | Create a grant for a key |
| `create-key` | Keys | Create a new KMS key |
| `decrypt` | Crypto Ops | Decrypt ciphertext |
| `delete-alias` | Aliases | Delete an alias |
| `delete-custom-key-store` | Custom Key Stores | Delete a custom key store |
| `delete-imported-key-material` | Import | Delete imported key material |
| `derive-shared-secret` | Crypto Ops | Derive a shared secret via ECDH |
| `describe-custom-key-stores` | Custom Key Stores | Describe custom key stores |
| `describe-key` | Keys | Describe key metadata |
| `disable-key` | Keys | Disable a KMS key |
| `disable-key-rotation` | Rotation | Disable automatic key rotation |
| `disconnect-custom-key-store` | Custom Key Stores | Disconnect a custom key store |
| `enable-key` | Keys | Enable a KMS key |
| `enable-key-rotation` | Rotation | Enable automatic key rotation |
| `encrypt` | Crypto Ops | Encrypt plaintext |
| `generate-data-key` | Crypto Ops | Generate a data key (plaintext + encrypted) |
| `generate-data-key-pair` | Crypto Ops | Generate an asymmetric data key pair |
| `generate-data-key-pair-without-plaintext` | Crypto Ops | Generate data key pair (encrypted private key only) |
| `generate-data-key-without-plaintext` | Crypto Ops | Generate a data key (encrypted only) |
| `generate-mac` | Crypto Ops | Generate an HMAC tag |
| `generate-random` | Crypto Ops | Generate random bytes |
| `get-key-policy` | Keys | Get key policy document |
| `get-key-rotation-status` | Rotation | Get key rotation status |
| `get-parameters-for-import` | Import | Get wrapping key and import token |
| `get-public-key` | Keys | Get public key of asymmetric KMS key |
| `import-key-material` | Import | Import key material into a KMS key |
| `list-aliases` | Aliases | List all aliases |
| `list-grants` | Grants | List grants for a key |
| `list-key-policies` | Keys | List key policy names |
| `list-key-rotations` | Rotation | List key rotations |
| `list-keys` | Keys | List all KMS keys |
| `list-resource-tags` | Tags | List tags on a key |
| `list-retirable-grants` | Grants | List grants retirable by a principal |
| `put-key-policy` | Keys | Set key policy document |
| `re-encrypt` | Crypto Ops | Re-encrypt ciphertext under a different key |
| `replicate-key` | Multi-Region | Create a replica of a multi-region key |
| `retire-grant` | Grants | Retire a grant |
| `revoke-grant` | Grants | Revoke a grant |
| `rotate-key-on-demand` | Rotation | Trigger on-demand key rotation |
| `schedule-key-deletion` | Keys | Schedule a key for deletion |
| `sign` | Crypto Ops | Create a digital signature |
| `tag-resource` | Tags | Add tags to a key |
| `untag-resource` | Tags | Remove tags from a key |
| `update-alias` | Aliases | Update alias target key |
| `update-custom-key-store` | Custom Key Stores | Update custom key store settings |
| `update-key-description` | Keys | Update key description |
| `update-primary-region` | Multi-Region | Change primary region for multi-region key |
| `verify` | Crypto Ops | Verify a digital signature |
| `verify-mac` | Crypto Ops | Verify an HMAC tag |

---

---

# Global Options Reference

These options are available on every `aws kms` subcommand:

| Option | Type | Description |
|--------|------|-------------|
| `--debug` | boolean | Enable debug logging |
| `--endpoint-url` | string | Override default service endpoint |
| `--no-verify-ssl` | boolean | Disable SSL certificate verification |
| `--no-paginate` | boolean | Disable automatic pagination |
| `--output` | string | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | JMESPath query to filter output |
| `--profile` | string | AWS credential profile name |
| `--region` | string | AWS region |
| `--version` | | Display CLI version |
| `--color` | string | Color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | Do not sign requests (anonymous access) |
| `--ca-bundle` | string | CA certificate bundle for SSL verification |
| `--cli-read-timeout` | integer | Max socket read time in seconds (default: 60) |
| `--cli-connect-timeout` | integer | Max socket connect time in seconds (default: 60) |
| `--cli-binary-format` | string | Binary blob format: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | Disable CLI pager for output |
| `--cli-auto-prompt` | boolean | Automatically prompt for CLI input parameters |
| `--no-cli-auto-prompt` | boolean | Disable auto-prompt |
| `--cli-input-json` | string | Read arguments from JSON string |
| `--cli-input-yaml` | string | Read arguments from YAML string |
| `--generate-cli-skeleton` | string | Print JSON/YAML skeleton: `input`, `output`, `yaml-input` |
