# AWS CLI v2 — IAM Identity Center (SSO Admin + Identity Store)

## Overview

Complete reference for `aws sso-admin` and `aws identitystore` subcommands in AWS CLI v2. AWS IAM Identity Center (successor to AWS Single Sign-On) provides centralized access management for AWS accounts and applications. The `sso-admin` namespace manages instances, permission sets, account assignments, applications, and trusted token issuers. The `identitystore` namespace manages users and groups in the Identity Center directory.

## Quick Reference — Common Workflows

### Create a permission set
```bash
aws sso-admin create-permission-set \
  --instance-arn arn:aws:sso:::instance/ssoins-1234567890abcdef \
  --name AdminAccess \
  --session-duration PT8H
```

### Attach a managed policy to a permission set
```bash
aws sso-admin attach-managed-policy-to-permission-set \
  --instance-arn arn:aws:sso:::instance/ssoins-1234567890abcdef \
  --permission-set-arn arn:aws:sso:::permissionSet/ssoins-1234567890abcdef/ps-1234567890abcdef \
  --managed-policy-arn arn:aws:iam::aws:policy/AdministratorAccess
```

### Assign a group to an AWS account
```bash
aws sso-admin create-account-assignment \
  --instance-arn arn:aws:sso:::instance/ssoins-1234567890abcdef \
  --target-id 123456789012 \
  --target-type AWS_ACCOUNT \
  --permission-set-arn arn:aws:sso:::permissionSet/ssoins-1234567890abcdef/ps-1234567890abcdef \
  --principal-type GROUP \
  --principal-id 12345678-1234-1234-1234-123456789012
```

### Provision a permission set
```bash
aws sso-admin provision-permission-set \
  --instance-arn arn:aws:sso:::instance/ssoins-1234567890abcdef \
  --permission-set-arn arn:aws:sso:::permissionSet/ssoins-1234567890abcdef/ps-1234567890abcdef \
  --target-type ALL_PROVISIONED_ACCOUNTS
```

### Create a user in the identity store
```bash
aws identitystore create-user \
  --identity-store-id d-1234567890 \
  --user-name jdoe \
  --name '{"GivenName":"John","FamilyName":"Doe"}' \
  --display-name "John Doe" \
  --emails '[{"Value":"jdoe@example.com","Type":"work","Primary":true}]'
```

### Create a group and add a member
```bash
aws identitystore create-group \
  --identity-store-id d-1234567890 \
  --display-name Developers

aws identitystore create-group-membership \
  --identity-store-id d-1234567890 \
  --group-id 12345678-1234-1234-1234-123456789012 \
  --member-id '{"UserId":"abcdefgh-1234-1234-1234-123456789012"}'
```

### List all permission sets
```bash
aws sso-admin list-permission-sets \
  --instance-arn arn:aws:sso:::instance/ssoins-1234567890abcdef
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Instances | [`instances.md`](instances.md) | create-instance, delete-instance, describe-instance, list-instances, update-instance, create-instance-access-control-attribute-configuration, delete-instance-access-control-attribute-configuration, describe-instance-access-control-attribute-configuration, update-instance-access-control-attribute-configuration, add-region, remove-region, describe-region, list-regions |
| Permission Sets | [`permission-sets.md`](permission-sets.md) | create-permission-set, delete-permission-set, describe-permission-set, update-permission-set, list-permission-sets, list-permission-sets-provisioned-to-account, list-accounts-for-provisioned-permission-set, provision-permission-set, describe-permission-set-provisioning-status, list-permission-set-provisioning-status |
| Permission Set Policies | [`permission-set-policies.md`](permission-set-policies.md) | attach-managed-policy-to-permission-set, detach-managed-policy-from-permission-set, list-managed-policies-in-permission-set, attach-customer-managed-policy-reference-to-permission-set, detach-customer-managed-policy-reference-from-permission-set, list-customer-managed-policy-references-in-permission-set, put-inline-policy-to-permission-set, get-inline-policy-for-permission-set, delete-inline-policy-from-permission-set, put-permissions-boundary-to-permission-set, get-permissions-boundary-for-permission-set, delete-permissions-boundary-from-permission-set |
| Account Assignments | [`account-assignments.md`](account-assignments.md) | create-account-assignment, delete-account-assignment, list-account-assignments, list-account-assignments-for-principal, describe-account-assignment-creation-status, list-account-assignment-creation-status, describe-account-assignment-deletion-status, list-account-assignment-deletion-status |
| Applications | [`applications.md`](applications.md) | create-application, delete-application, describe-application, update-application, list-applications, list-application-providers, create-application-assignment, delete-application-assignment, describe-application-assignment, list-application-assignments, list-application-assignments-for-principal |
| Application Config | [`application-config.md`](application-config.md) | put-application-access-scope, get-application-access-scope, delete-application-access-scope, list-application-access-scopes, put-application-assignment-configuration, get-application-assignment-configuration, put-application-authentication-method, get-application-authentication-method, delete-application-authentication-method, list-application-authentication-methods, put-application-grant, get-application-grant, delete-application-grant, list-application-grants, put-application-session-configuration, get-application-session-configuration, describe-application-provider |
| Trusted Token Issuers | [`trusted-token-issuers.md`](trusted-token-issuers.md) | create-trusted-token-issuer, delete-trusted-token-issuer, describe-trusted-token-issuer, update-trusted-token-issuer, list-trusted-token-issuers |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| Identity Store Users | [`identity-store-users.md`](identity-store-users.md) | create-user, delete-user, describe-user, update-user, get-user-id, list-users |
| Identity Store Groups | [`identity-store-groups.md`](identity-store-groups.md) | create-group, delete-group, describe-group, update-group, get-group-id, list-groups, create-group-membership, delete-group-membership, describe-group-membership, get-group-membership-id, is-member-in-groups, list-group-memberships, list-group-memberships-for-member |
