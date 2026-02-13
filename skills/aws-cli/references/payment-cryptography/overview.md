# AWS CLI v2 — Payment Cryptography

## Overview

Complete reference for all `aws payment-cryptography` and `aws payment-cryptography-data` subcommands in AWS CLI v2. Covers payment HSM key management (creation, import/export, aliases, replication) and cryptographic data operations (encryption/decryption, PIN generation/verification, MAC generation/verification, and card validation). This is a merged reference combining both the control plane (`payment-cryptography`) and data plane (`payment-cryptography-data`) CLI namespaces.

## Quick Reference — Common Workflows

### Create a symmetric encryption key
```bash
aws payment-cryptography create-key \
  --exportable \
  --key-attributes KeyAlgorithm=TDES_2KEY,KeyUsage=TR31_C0_CARD_VERIFICATION_KEY,KeyClass=SYMMETRIC_KEY,KeyModesOfUse='{Generate=true,Verify=true}'
```

### Encrypt data with a symmetric key
```bash
aws payment-cryptography-data encrypt-data \
  --key-identifier arn:aws:payment-cryptography:us-east-2:123456789012:key/kwapwa6qaifllw2h \
  --plain-text 31323334313233343132333431323334 \
  --encryption-attributes 'Symmetric={Mode=CBC}'
```

### Generate a PIN
```bash
aws payment-cryptography-data generate-pin-data \
  --generation-key-identifier arn:aws:payment-cryptography:us-east-2:111122223333:key/37y2tsl45p5zjbh2 \
  --encryption-key-identifier arn:aws:payment-cryptography:us-east-2:111122223333:key/ivi5ksfsuplneuyt \
  --primary-account-number 171234567890123 \
  --pin-block-format ISO_FORMAT_0 \
  --generation-attributes VisaPin={PinVerificationKeyIndex=1}
```

### Generate a MAC
```bash
aws payment-cryptography-data generate-mac \
  --key-identifier arn:aws:payment-cryptography:us-east-2:123456789012:key/kwapwa6qaifllw2h \
  --message-data "3b313038383439303031303733393431353d32343038323236303030373030303f33" \
  --generation-attributes Algorithm=HMAC_SHA256
```

### Create an alias for a key
```bash
aws payment-cryptography create-alias \
  --alias-name alias/myPaymentKey \
  --key-arn arn:aws:payment-cryptography:us-east-2:123456789012:key/kwapwa6qaifllw2h
```

### Generate card validation data (CVV)
```bash
aws payment-cryptography-data generate-card-validation-data \
  --key-identifier arn:aws:payment-cryptography:us-east-2:123456789012:key/kwapwa6qaifllw2h \
  --primary-account-number 171234567890123 \
  --generation-attributes CardVerificationValue2={CardExpiryDate=0123}
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Keys | [`keys.md`](keys.md) | `payment-cryptography`: create-key, delete-key, get-key, list-keys, start-key-usage, stop-key-usage, restore-key, get-public-key-certificate, get-certificate-signing-request |
| Key Import/Export | [`key-import-export.md`](key-import-export.md) | `payment-cryptography`: import-key, export-key, get-parameters-for-import, get-parameters-for-export |
| Aliases | [`aliases.md`](aliases.md) | `payment-cryptography`: create-alias, delete-alias, get-alias, list-aliases, update-alias |
| Key Replication | [`key-replication.md`](key-replication.md) | `payment-cryptography`: add-key-replication-regions, remove-key-replication-regions, get-default-key-replication-regions, enable-default-key-replication-regions, disable-default-key-replication-regions |
| Encryption | [`encryption.md`](encryption.md) | `payment-cryptography-data`: encrypt-data, decrypt-data, re-encrypt-data |
| PIN Operations | [`pin-operations.md`](pin-operations.md) | `payment-cryptography-data`: generate-pin-data, verify-pin-data, translate-pin-data, generate-mac-emv-pin-change |
| MAC Operations | [`mac-operations.md`](mac-operations.md) | `payment-cryptography-data`: generate-mac, verify-mac |
| Card Validation | [`card-validation.md`](card-validation.md) | `payment-cryptography-data`: generate-card-validation-data, verify-card-validation-data, verify-auth-request-cryptogram, generate-as2805-kek-validation, translate-key-material |
| Tags | [`tags.md`](tags.md) | `payment-cryptography`: tag-resource, untag-resource, list-tags-for-resource |
