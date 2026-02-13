# AWS CLI v2 — ACM (AWS Certificate Manager)

## Overview

Complete reference for all `aws acm` subcommands in AWS CLI v2. Covers certificate request and management, import/export of certificates, tagging, and account-level configuration.

## Quick Reference — Common Workflows

### Request a public certificate with DNS validation
```bash
aws acm request-certificate --domain-name example.com \
  --validation-method DNS \
  --subject-alternative-names "*.example.com" \
  --key-algorithm RSA_2048
```

### Get DNS validation records
```bash
aws acm describe-certificate --certificate-arn arn:aws:acm:us-east-1:123456789012:certificate/abc-123 \
  --query 'Certificate.DomainValidationOptions[].ResourceRecord'
```

### Import a third-party certificate
```bash
aws acm import-certificate \
  --certificate fileb://cert.pem \
  --private-key fileb://key.pem \
  --certificate-chain fileb://chain.pem
```

### List all issued certificates
```bash
aws acm list-certificates --certificate-statuses ISSUED \
  --query 'CertificateSummaryList[].{ARN:CertificateArn,Domain:DomainName}'
```

### Export a private certificate
```bash
aws acm export-certificate \
  --certificate-arn arn:aws:acm:us-east-1:123456789012:certificate/abc-123 \
  --passphrase fileb://passphrase.txt
```

### Wait for certificate to be issued
```bash
aws acm wait certificate-validated \
  --certificate-arn arn:aws:acm:us-east-1:123456789012:certificate/abc-123
```

### Delete a certificate
```bash
aws acm delete-certificate \
  --certificate-arn arn:aws:acm:us-east-1:123456789012:certificate/abc-123
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Certificates | [`certificates.md`](certificates.md) | request-certificate, describe-certificate, delete-certificate, list-certificates, renew-certificate, resend-validation-email |
| Import & Export | [`import-export.md`](import-export.md) | import-certificate, export-certificate, get-certificate |
| Tags | [`tags.md`](tags.md) | add-tags-to-certificate, remove-tags-from-certificate, list-tags-for-certificate |
| Account | [`account.md`](account.md) | get-account-configuration, put-account-configuration |
