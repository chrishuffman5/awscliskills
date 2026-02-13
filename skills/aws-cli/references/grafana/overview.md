# AWS CLI v2 — Amazon Managed Grafana

## Overview

Complete reference for all `aws grafana` subcommands in AWS CLI v2. Covers managed Grafana workspace lifecycle (create, update, delete, describe), workspace configuration, authentication (SAML, IAM Identity Center), permissions management, service accounts, API keys, license association, and tagging.

## Quick Reference — Common Workflows

### Create a workspace
```bash
aws grafana create-workspace \
  --account-access-type CURRENT_ACCOUNT \
  --authentication-providers SAML \
  --permission-type SERVICE_MANAGED \
  --workspace-name my-grafana \
  --workspace-data-sources CLOUDWATCH,PROMETHEUS
```

### List workspaces
```bash
aws grafana list-workspaces
```

### Describe a workspace
```bash
aws grafana describe-workspace --workspace-id g-abc123
```

### Update workspace authentication (enable SAML)
```bash
aws grafana update-workspace-authentication \
  --workspace-id g-abc123 \
  --authentication-providers SAML \
  --saml-configuration '{"idpMetadata":{"url":"https://idp.example.com/metadata"},"assertionAttributes":{"email":"mail","name":"displayName"}}'
```

### Create a service account
```bash
aws grafana create-workspace-service-account \
  --workspace-id g-abc123 \
  --name my-service-account \
  --grafana-role ADMIN
```

### Create a service account token
```bash
aws grafana create-workspace-service-account-token \
  --workspace-id g-abc123 \
  --service-account-id sa-abc123 \
  --name my-token \
  --seconds-to-live 86400
```

### Update permissions
```bash
aws grafana update-permissions \
  --workspace-id g-abc123 \
  --update-instruction-batch '[{"action":"ADD","role":"ADMIN","users":[{"id":"user-id","type":"SSO_USER"}]}]'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Workspaces | [`workspaces.md`](workspaces.md) | create-workspace, delete-workspace, describe-workspace, list-workspaces, update-workspace, describe-workspace-configuration, update-workspace-configuration, list-versions |
| Authentication | [`authentication.md`](authentication.md) | describe-workspace-authentication, update-workspace-authentication |
| Permissions | [`permissions.md`](permissions.md) | list-permissions, update-permissions |
| Service Accounts | [`service-accounts.md`](service-accounts.md) | create-workspace-service-account, delete-workspace-service-account, list-workspace-service-accounts, create-workspace-service-account-token, delete-workspace-service-account-token, list-workspace-service-account-tokens |
| API Keys & Licenses | [`api-keys-licenses.md`](api-keys-licenses.md) | create-workspace-api-key, delete-workspace-api-key, associate-license, disassociate-license |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
