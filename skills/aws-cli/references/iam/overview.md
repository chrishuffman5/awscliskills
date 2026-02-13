
# AWS CLI v2 — IAM (Identity and Access Management)

## Overview

Complete reference for all `aws iam` subcommands in AWS CLI v2. Covers user and group management, role creation and assumption, policy authoring and attachment, instance profiles for EC2/ECS, access key rotation, MFA configuration, and identity providers (OIDC, SAML).

## Quick Reference — Common Workflows

### Create a role for ECS tasks
```bash
aws iam create-role --role-name ecsTaskRole \
  --assume-role-policy-document '{
    "Version":"2012-10-17",
    "Statement":[{"Effect":"Allow","Principal":{"Service":"ecs-tasks.amazonaws.com"},"Action":"sts:AssumeRole"}]
  }'
aws iam attach-role-policy --role-name ecsTaskRole \
  --policy-arn arn:aws:iam::aws:policy/service-role/AmazonECSTaskExecutionRolePolicy
```

### Create instance profile for ECS EC2 instances
```bash
aws iam create-instance-profile --instance-profile-name ecsInstanceProfile
aws iam add-role-to-instance-profile --instance-profile-name ecsInstanceProfile --role-name ecsInstanceRole
```

### Create a policy and attach to role
```bash
aws iam create-policy --policy-name my-policy --policy-document file://policy.json
aws iam attach-role-policy --role-name my-role --policy-arn arn:aws:iam::123456789012:policy/my-policy
```

### List and rotate access keys
```bash
aws iam list-access-keys --user-name my-user
aws iam create-access-key --user-name my-user
aws iam delete-access-key --user-name my-user --access-key-id AKIA...
```

### Get account authorization details
```bash
aws iam get-account-authorization-details --filter Role --query 'RoleDetailList[].{Name:RoleName,Arn:Arn}'
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Users | create, delete, get, list, update, tag/untag | User lifecycle |
| Groups | create, delete, get, list, add/remove user | Group membership |
| Roles | create, delete, get, list, update, tag/untag | Role management |
| Policies | create, delete, get, list, create-version, set-default-version | Managed policies |
| Policy Attachment | attach/detach role/user/group policy, list attached/entities | Binding policies |
| Inline Policies | put/get/delete role/user/group policy, list role/user/group policies | Embedded policies |
| Instance Profiles | create, delete, get, list, add/remove role | EC2/ECS instance profiles |
| Access Keys | create, delete, list, update, get-last-used | Credential management |
| MFA | create/delete/deactivate/enable/list virtual MFA, resync | Multi-factor auth |
| Identity Providers | create/delete/get/list/update OIDC and SAML providers | Federation |
| Service-Linked Roles | create, delete, get-deletion-status | AWS-managed roles |
| Account | get-account-summary, get-account-authorization-details, generate-credential-report, get-credential-report | Account audit |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Users | [`users.md`](users.md) | create-user, get-user, list-users, update-user, delete-user |
| Groups | [`groups.md`](groups.md) | create-group, get-group, list-groups, update-group, delete-group, add-user-to-group, remove-user-from-group, list-groups-for-user |
| Roles | [`roles.md`](roles.md) | create-role, get-role, list-roles, update-role, update-role-description, update-assume-role-policy, delete-role |
| Managed Policies | [`managed-policies.md`](managed-policies.md) | create-policy, get-policy, list-policies, create-policy-version, get-policy-version, list-policy-versions, set-default-policy-version, delete-policy-version, delete-policy |
| Policy Attachment | [`policy-attachment.md`](policy-attachment.md) | attach-role-policy, detach-role-policy, attach-user-policy, detach-user-policy, attach-group-policy, detach-group-policy, list-attached-role-policies, list-attached-user-policies, list-attached-group-policies, list-entities-for-policy |
| Inline Policies | [`inline-policies.md`](inline-policies.md) | put-role-policy, get-role-policy, delete-role-policy, list-role-policies, put-user-policy, get-user-policy, delete-user-policy, list-user-policies, put-group-policy, get-group-policy, delete-group-policy, list-group-policies |
| Instance Profiles | [`instance-profiles.md`](instance-profiles.md) | create-instance-profile, get-instance-profile, list-instance-profiles, list-instance-profiles-for-role, add-role-to-instance-profile, remove-role-from-instance-profile, delete-instance-profile |
| Access Keys | [`access-keys.md`](access-keys.md) | create-access-key, list-access-keys, get-access-key-last-used, update-access-key, delete-access-key |
| Login Profiles | [`login-profiles.md`](login-profiles.md) | create-login-profile, get-login-profile, update-login-profile, delete-login-profile |
| MFA Devices | [`mfa-devices.md`](mfa-devices.md) | create-virtual-mfa-device, enable-mfa-device, deactivate-mfa-device, delete-virtual-mfa-device, list-mfa-devices, list-virtual-mfa-devices, resync-mfa-device, get-mfa-device |
| Signing Certificates | [`signing-certificates.md`](signing-certificates.md) | upload-signing-certificate, list-signing-certificates, update-signing-certificate, delete-signing-certificate |
| SSH Public Keys | [`ssh-public-keys.md`](ssh-public-keys.md) | upload-ssh-public-key, get-ssh-public-key, list-ssh-public-keys, update-ssh-public-key, delete-ssh-public-key |
| Server Certificates | [`server-certificates.md`](server-certificates.md) | upload-server-certificate, get-server-certificate, list-server-certificates, update-server-certificate, delete-server-certificate |
| OIDC Providers | [`oidc-providers.md`](oidc-providers.md) | create-open-id-connect-provider, get-open-id-connect-provider, list-open-id-connect-providers, add-client-id-to-open-id-connect-provider, remove-client-id-from-open-id-connect-provider, update-open-id-connect-provider-thumbprint, delete-open-id-connect-provider |
| SAML Providers | [`saml-providers.md`](saml-providers.md) | create-saml-provider, get-saml-provider, list-saml-providers, update-saml-provider, delete-saml-provider |
| Service-Linked Roles | [`service-linked-roles.md`](service-linked-roles.md) | create-service-linked-role, delete-service-linked-role, get-service-linked-role-deletion-status |
| Service-Specific Credentials | [`service-specific-credentials.md`](service-specific-credentials.md) | create-service-specific-credential, list-service-specific-credentials, update-service-specific-credential, reset-service-specific-credential, delete-service-specific-credential |
| Permissions Boundaries | [`permissions-boundaries.md`](permissions-boundaries.md) | put-role-permissions-boundary, delete-role-permissions-boundary, put-user-permissions-boundary, delete-user-permissions-boundary |
| Account & Reporting | [`account-reporting.md`](account-reporting.md) | get-account-summary, get-account-authorization-details, generate-credential-report, get-credential-report, get-account-password-policy, update-account-password-policy, delete-account-password-policy, create-account-alias, list-account-aliases, delete-account-alias, generate-service-last-accessed-details, get-service-last-accessed-details, get-service-last-accessed-details-with-entities, set-security-token-service-preferences, list-policies-granting-service-access |
| Policy Simulation | [`policy-simulation.md`](policy-simulation.md) | simulate-principal-policy, simulate-custom-policy, get-context-keys-for-principal-policy, get-context-keys-for-custom-policy |
| Tags | [`tags.md`](tags.md) | tag-user, tag-role, tag-policy, tag-instance-profile, tag-mfa-device, tag-open-id-connect-provider, tag-saml-provider, tag-server-certificate, untag-user, untag-role, untag-policy, untag-instance-profile, untag-mfa-device, untag-open-id-connect-provider, untag-saml-provider, untag-server-certificate, list-user-tags, list-role-tags, list-policy-tags, list-instance-profile-tags, list-mfa-device-tags, list-open-id-connect-provider-tags, list-saml-provider-tags, list-server-certificate-tags |
