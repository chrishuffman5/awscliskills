# AWS CLI v2 — STS (Security Token Service)

## Overview

Complete reference for all `aws sts` subcommands in AWS CLI v2. Covers assuming IAM roles, generating temporary security credentials, retrieving caller identity, decoding authorization messages, and federating access for external identities.

## Quick Reference — Common Workflows

### Get caller identity
```bash
aws sts get-caller-identity
```

### Assume an IAM role
```bash
aws sts assume-role \
  --role-arn arn:aws:iam::123456789012:role/MyRole \
  --role-session-name my-session \
  --duration-seconds 3600
```

### Assume a role with an external ID (cross-account)
```bash
aws sts assume-role \
  --role-arn arn:aws:iam::987654321098:role/CrossAccountRole \
  --role-session-name cross-acct \
  --external-id my-external-id
```

### Get temporary session token (MFA)
```bash
aws sts get-session-token \
  --serial-number arn:aws:iam::123456789012:mfa/user \
  --token-code 123456 \
  --duration-seconds 3600
```

### Assume role with web identity (OIDC)
```bash
aws sts assume-role-with-web-identity \
  --role-arn arn:aws:iam::123456789012:role/WebRole \
  --role-session-name web-session \
  --web-identity-token file://token.txt
```

### Use assumed role credentials
```bash
# Parse credentials from assume-role output
eval $(aws sts assume-role \
  --role-arn arn:aws:iam::123456789012:role/MyRole \
  --role-session-name my-session \
  --query 'Credentials.[AccessKeyId,SecretAccessKey,SessionToken]' \
  --output text | \
  awk '{print "export AWS_ACCESS_KEY_ID="$1" AWS_SECRET_ACCESS_KEY="$2" AWS_SESSION_TOKEN="$3}')
```

### Decode an authorization error message
```bash
aws sts decode-authorization-message \
  --encoded-message <encoded-message-string>
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Assume Role | [`assume-role.md`](assume-role.md) | assume-role, assume-role-with-saml, assume-role-with-web-identity |
| Credentials | [`credentials.md`](credentials.md) | get-session-token, get-federation-token, get-access-key-info |
| Identity | [`identity.md`](identity.md) | get-caller-identity, decode-authorization-message |
