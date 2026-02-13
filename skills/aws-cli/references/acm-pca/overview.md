# AWS CLI v2 — Private CA (AWS Private Certificate Authority)

## Overview

Complete reference for all `aws acm-pca` subcommands in AWS CLI v2. Covers private certificate authority lifecycle management, certificate issuance and revocation, CSR generation, audit report creation, CA permission and policy management, and tagging.

## Quick Reference — Common Workflows

### Create a root CA
```bash
aws acm-pca create-certificate-authority \
  --certificate-authority-configuration \
    KeyAlgorithm=RSA_2048,SigningAlgorithm=SHA256WITHRSA,Subject={CommonName="My Root CA",Organization="MyOrg",Country=US} \
  --certificate-authority-type ROOT \
  --tags Key=Environment,Value=production
```

### Get the CA CSR and install the CA certificate
```bash
# Get the CSR
aws acm-pca get-certificate-authority-csr \
  --certificate-authority-arn arn:aws:acm-pca:us-east-1:123456789012:certificate-authority/12345678-1234-1234-1234-123456789012 \
  --output text > ca.csr

# Self-sign for root CA
aws acm-pca issue-certificate \
  --certificate-authority-arn arn:aws:acm-pca:us-east-1:123456789012:certificate-authority/12345678-1234-1234-1234-123456789012 \
  --csr fileb://ca.csr \
  --signing-algorithm SHA256WITHRSA \
  --template-arn arn:aws:acm-pca:::template/RootCACertificate/V1 \
  --validity Value=3650,Type=DAYS

# Wait for certificate to be issued
aws acm-pca wait certificate-issued \
  --certificate-authority-arn arn:aws:acm-pca:us-east-1:123456789012:certificate-authority/12345678-1234-1234-1234-123456789012 \
  --certificate-arn "$CERT_ARN"

# Import the CA certificate
aws acm-pca import-certificate-authority-certificate \
  --certificate-authority-arn arn:aws:acm-pca:us-east-1:123456789012:certificate-authority/12345678-1234-1234-1234-123456789012 \
  --certificate fileb://ca-cert.pem
```

### Issue an end-entity certificate
```bash
aws acm-pca issue-certificate \
  --certificate-authority-arn arn:aws:acm-pca:us-east-1:123456789012:certificate-authority/12345678-1234-1234-1234-123456789012 \
  --csr fileb://server.csr \
  --signing-algorithm SHA256WITHRSA \
  --validity Value=365,Type=DAYS
```

### Retrieve an issued certificate
```bash
aws acm-pca get-certificate \
  --certificate-authority-arn "$CA_ARN" \
  --certificate-arn "$CERT_ARN" \
  --output text
```

### Revoke a certificate
```bash
aws acm-pca revoke-certificate \
  --certificate-authority-arn "$CA_ARN" \
  --certificate-serial "serial-number" \
  --revocation-reason KEY_COMPROMISE
```

### Create an audit report
```bash
aws acm-pca create-certificate-authority-audit-report \
  --certificate-authority-arn "$CA_ARN" \
  --s3-bucket-name my-audit-bucket \
  --audit-report-response-format JSON
```

### Disable and delete a CA
```bash
aws acm-pca update-certificate-authority \
  --certificate-authority-arn "$CA_ARN" \
  --status DISABLED

aws acm-pca delete-certificate-authority \
  --certificate-authority-arn "$CA_ARN" \
  --permanent-deletion-time-in-days 7
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Certificate Authorities | [`certificate-authorities.md`](certificate-authorities.md) | create-certificate-authority, delete-certificate-authority, describe-certificate-authority, list-certificate-authorities, update-certificate-authority, restore-certificate-authority, get-certificate-authority-certificate, get-certificate-authority-csr, import-certificate-authority-certificate |
| Certificates | [`certificates.md`](certificates.md) | issue-certificate, get-certificate, revoke-certificate |
| Audit Reports | [`audit-reports.md`](audit-reports.md) | create-certificate-authority-audit-report, describe-certificate-authority-audit-report |
| Permissions & Policies | [`permissions-policies.md`](permissions-policies.md) | create-permission, delete-permission, list-permissions, get-policy, put-policy, delete-policy |
| Tags | [`tags.md`](tags.md) | tag-certificate-authority, untag-certificate-authority, list-tags |
| Wait | [`wait.md`](wait.md) | wait audit-report-created, wait certificate-authority-csr-created, wait certificate-issued |
