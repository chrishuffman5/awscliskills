# AWS CLI v2 — Cognito (User Pools + Identity Pools)

## Overview

Complete reference for `aws cognito-idp` (Cognito User Pools) and `aws cognito-identity` (Cognito Identity Pools) subcommands in AWS CLI v2. Covers user pool management, user pool clients, user management, groups, identity providers, identity pools (federated identities), MFA configuration, custom domains, and resource servers.

## Quick Reference — Common Workflows

### Create a user pool
```bash
aws cognito-idp create-user-pool --pool-name my-user-pool \
  --auto-verified-attributes email \
  --schema Name=email,Required=true,Mutable=true
```

### Create a user pool client
```bash
aws cognito-idp create-user-pool-client \
  --user-pool-id us-east-1_abc123 \
  --client-name my-web-app \
  --explicit-auth-flows ALLOW_USER_PASSWORD_AUTH ALLOW_REFRESH_TOKEN_AUTH \
  --generate-secret
```

### Create a user (admin)
```bash
aws cognito-idp admin-create-user \
  --user-pool-id us-east-1_abc123 \
  --username john@example.com \
  --user-attributes Name=email,Value=john@example.com Name=email_verified,Value=true \
  --temporary-password "TempP@ss123"
```

### Set permanent password (admin)
```bash
aws cognito-idp admin-set-user-password \
  --user-pool-id us-east-1_abc123 \
  --username john@example.com \
  --password "NewP@ss456" \
  --permanent
```

### Add a user to a group
```bash
aws cognito-idp admin-add-user-to-group \
  --user-pool-id us-east-1_abc123 \
  --username john@example.com \
  --group-name Admins
```

### Configure MFA for a user pool
```bash
aws cognito-idp set-user-pool-mfa-config \
  --user-pool-id us-east-1_abc123 \
  --software-token-mfa-configuration Enabled=true \
  --mfa-configuration ON
```

### Create an identity pool (federated identities)
```bash
aws cognito-identity create-identity-pool \
  --identity-pool-name my-identity-pool \
  --allow-unauthenticated-identities \
  --cognito-identity-providers ProviderName=cognito-idp.us-east-1.amazonaws.com/us-east-1_abc123,ClientId=client123,ServerSideTokenCheck=true
```

### Set up a custom domain
```bash
aws cognito-idp create-user-pool-domain \
  --user-pool-id us-east-1_abc123 \
  --domain my-app-domain
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| User Pools | [`user-pools.md`](user-pools.md) | create-user-pool, delete-user-pool, describe-user-pool, list-user-pools, update-user-pool |
| User Pool Clients | [`user-pool-clients.md`](user-pool-clients.md) | create-user-pool-client, delete-user-pool-client, describe-user-pool-client, list-user-pool-clients, update-user-pool-client |
| Users | [`users.md`](users.md) | admin-create-user, admin-delete-user, admin-get-user, admin-set-user-password, admin-confirm-sign-up, admin-disable-user, admin-enable-user, admin-update-user-attributes, list-users, sign-up, confirm-sign-up, forgot-password, confirm-forgot-password |
| Groups | [`groups.md`](groups.md) | create-group, delete-group, get-group, list-groups, update-group, admin-add-user-to-group, admin-remove-user-from-group, admin-list-groups-for-user, list-users-in-group |
| Identity Providers | [`identity-providers.md`](identity-providers.md) | create-identity-provider, delete-identity-provider, describe-identity-provider, list-identity-providers, update-identity-provider |
| Identity Pools | [`identity-pools.md`](identity-pools.md) | create-identity-pool, delete-identity-pool, describe-identity-pool, list-identity-pools, update-identity-pool, get-id, get-credentials-for-identity, get-open-id-token-for-developer-identity, set-identity-pool-roles, get-identity-pool-roles |
| MFA | [`mfa.md`](mfa.md) | set-user-pool-mfa-config, get-user-pool-mfa-config, admin-set-user-mfa-preference, set-user-mfa-preference, associate-software-token, verify-software-token |
| Domains | [`domains.md`](domains.md) | create-user-pool-domain, delete-user-pool-domain, describe-user-pool-domain, update-user-pool-domain |
| Resource Servers | [`resource-servers.md`](resource-servers.md) | create-resource-server, delete-resource-server, describe-resource-server, list-resource-servers, update-resource-server |
