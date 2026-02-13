
# AWS CLI v2 — KMS (Key Management Service)

## Overview

Complete reference for all `aws kms` subcommands in AWS CLI v2. Covers symmetric and asymmetric key creation, key policies, grants, aliases, encrypt/decrypt/sign/verify operations, automatic key rotation, multi-region keys, custom key stores (CloudHSM), and key material import.

## Quick Reference — Common Workflows

### Create a symmetric encryption key
```bash
aws kms create-key --description "My encryption key" \
  --key-usage ENCRYPT_DECRYPT --key-spec SYMMETRIC_DEFAULT
aws kms create-alias --alias-name alias/my-key --target-key-id <key-id>
```

### Encrypt and decrypt data
```bash
aws kms encrypt --key-id alias/my-key --plaintext fileb://plaintext.txt \
  --output text --query CiphertextBlob | base64 --decode > encrypted.bin
aws kms decrypt --ciphertext-blob fileb://encrypted.bin \
  --output text --query Plaintext | base64 --decode > decrypted.txt
```

### Generate a data key for envelope encryption
```bash
aws kms generate-data-key --key-id alias/my-key --key-spec AES_256
```

### Enable automatic key rotation
```bash
aws kms enable-key-rotation --key-id <key-id>
aws kms get-key-rotation-status --key-id <key-id>
```

### List all keys and aliases
```bash
aws kms list-keys --query 'Keys[].KeyId'
aws kms list-aliases --query 'Aliases[].{Alias:AliasName,Key:TargetKeyId}'
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Keys | create-key, describe-key, list-keys, enable-key, disable-key, schedule/cancel-key-deletion | Key lifecycle |
| Cryptographic Ops | encrypt, decrypt, re-encrypt, generate-data-key, generate-data-key-without-plaintext, generate-random, sign, verify, generate-mac, verify-mac | Data operations |
| Key Policies | get/put-key-policy, list-key-policies | Access control |
| Grants | create-grant, list-grants, list-retirable-grants, retire-grant, revoke-grant | Delegated access |
| Aliases | create-alias, delete-alias, list-aliases, update-alias | Friendly names |
| Rotation | enable/disable-key-rotation, get-key-rotation-status, rotate-key-on-demand | Key rotation |
| Multi-Region | replicate-key, update-primary-region | Cross-region keys |
| Custom Key Stores | create/delete/describe/update/connect/disconnect-custom-key-store | CloudHSM-backed |
| Import Key Material | get-parameters-for-import, import-key-material, delete-imported-key-material | External keys |
| Tags | tag-resource, untag-resource, list-resource-tags | Resource tagging |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Key Management | [`key-management.md`](key-management.md) | create-key, describe-key, list-keys, enable-key, disable-key, schedule-key-deletion, cancel-key-deletion, get-key-policy, put-key-policy, list-key-policies, get-public-key, update-key-description |
| Cryptographic Operations | [`cryptographic-operations.md`](cryptographic-operations.md) | encrypt, decrypt, re-encrypt, generate-data-key, generate-data-key-without-plaintext, generate-data-key-pair, generate-data-key-pair-without-plaintext, generate-random, sign, verify, generate-mac, verify-mac, derive-shared-secret |
| Grants | [`grants.md`](grants.md) | create-grant, list-grants, list-retirable-grants, retire-grant, revoke-grant |
| Aliases | [`aliases.md`](aliases.md) | create-alias, delete-alias, list-aliases, update-alias |
| Key Rotation | [`key-rotation.md`](key-rotation.md) | enable-key-rotation, disable-key-rotation, get-key-rotation-status, list-key-rotations, rotate-key-on-demand |
| Multi-Region Keys | [`multi-region-keys.md`](multi-region-keys.md) | replicate-key, update-primary-region |
| Custom Key Stores | [`custom-key-stores.md`](custom-key-stores.md) | create-custom-key-store, delete-custom-key-store, describe-custom-key-stores, update-custom-key-store, connect-custom-key-store, disconnect-custom-key-store |
| Import Key Material | [`import-key-material.md`](import-key-material.md) | get-parameters-for-import, import-key-material, delete-imported-key-material |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-resource-tags |
