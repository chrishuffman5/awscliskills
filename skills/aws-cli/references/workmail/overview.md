# AWS CLI v2 — WorkMail

## Overview

Complete reference for all `aws workmail` and `aws workmailmessageflow` subcommands in AWS CLI v2. Covers organization management, user/group/resource provisioning, mailbox operations, mail domain configuration, access control rules, impersonation roles, mobile device access policies, availability configurations, email monitoring, retention policies, Identity Center integration, personal access tokens, and message flow operations. Amazon WorkMail is a managed business email and calendar service with security and compliance controls.

## Quick Reference — Common Workflows

### Create an organization and register a domain
```bash
aws workmail create-organization \
    --alias my-org

aws workmail register-mail-domain \
    --organization-id m-d281d0a2fd824be5b6cd3d3ce909fd27 \
    --domain-name example.com

aws workmail update-default-mail-domain \
    --organization-id m-d281d0a2fd824be5b6cd3d3ce909fd27 \
    --domain-name example.com
```

### Create a user and register for WorkMail
```bash
aws workmail create-user \
    --organization-id m-d281d0a2fd824be5b6cd3d3ce909fd27 \
    --name jsmith \
    --display-name "John Smith" \
    --password 'MyP@ssw0rd!'

aws workmail register-to-work-mail \
    --organization-id m-d281d0a2fd824be5b6cd3d3ce909fd27 \
    --entity-id S-1-1-11-1111111111-2222222222-3333333333-3333 \
    --email jsmith@example.com
```

### Create a group and add members
```bash
aws workmail create-group \
    --organization-id m-d281d0a2fd824be5b6cd3d3ce909fd27 \
    --name engineering

aws workmail associate-member-to-group \
    --organization-id m-d281d0a2fd824be5b6cd3d3ce909fd27 \
    --group-id S-1-1-11-1122222222-2222233333-3333334444-4444 \
    --member-id S-1-1-11-1111111111-2222222222-3333333333-3333
```

### Create a room resource
```bash
aws workmail create-resource \
    --organization-id m-d281d0a2fd824be5b6cd3d3ce909fd27 \
    --name "ConferenceRoom1" \
    --type ROOM
```

### Set up access control rules
```bash
aws workmail put-access-control-rule \
    --organization-id m-d281d0a2fd824be5b6cd3d3ce909fd27 \
    --name "DenyExternalIMAP" \
    --effect DENY \
    --description "Deny IMAP from external IPs" \
    --actions IMAP \
    --not-ip-ranges "10.0.0.0/8"
```

### Export a mailbox to S3
```bash
aws workmail start-mailbox-export-job \
    --organization-id m-d281d0a2fd824be5b6cd3d3ce909fd27 \
    --entity-id S-1-1-11-1111111111-2222222222-3333333333-3333 \
    --role-arn arn:aws:iam::123456789012:role/MailboxExportRole \
    --kms-key-arn arn:aws:kms:us-east-1:123456789012:key/my-key \
    --s3-bucket-name my-export-bucket \
    --s3-prefix mailbox-exports/
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Organizations | [organizations.md](organizations.md) | `create-organization`, `describe-organization`, `list-organizations`, `delete-organization` |
| Users | [users.md](users.md) | `create-user`, `describe-user`, `list-users`, `update-user`, `delete-user`, `register-to-work-mail`, `deregister-from-work-mail`, `reset-password`, `describe-entity`, `list-groups-for-entity` |
| Groups | [groups.md](groups.md) | `create-group`, `describe-group`, `list-groups`, `update-group`, `delete-group`, `associate-member-to-group`, `disassociate-member-from-group`, `list-group-members` |
| Resources | [resources.md](resources.md) | `create-resource`, `describe-resource`, `list-resources`, `update-resource`, `delete-resource`, `associate-delegate-to-resource`, `disassociate-delegate-from-resource`, `list-resource-delegates` |
| Aliases & Email | [aliases.md](aliases.md) | `create-alias`, `delete-alias`, `list-aliases`, `update-primary-email-address` |
| Domains | [domains.md](domains.md) | `register-mail-domain`, `deregister-mail-domain`, `get-mail-domain`, `list-mail-domains`, `update-default-mail-domain`, `put-inbound-dmarc-settings`, `describe-inbound-dmarc-settings` |
| Mailbox | [mailbox.md](mailbox.md) | `get-mailbox-details`, `update-mailbox-quota`, `put-mailbox-permissions`, `delete-mailbox-permissions`, `list-mailbox-permissions`, `start-mailbox-export-job`, `describe-mailbox-export-job`, `cancel-mailbox-export-job`, `list-mailbox-export-jobs` |
| Access Control | [access-control.md](access-control.md) | `put-access-control-rule`, `list-access-control-rules`, `delete-access-control-rule`, `get-access-control-effect` |
| Impersonation | [impersonation.md](impersonation.md) | `create-impersonation-role`, `get-impersonation-role`, `list-impersonation-roles`, `update-impersonation-role`, `delete-impersonation-role`, `assume-impersonation-role`, `get-impersonation-role-effect` |
| Mobile Device Access | [mobile-device.md](mobile-device.md) | `create-mobile-device-access-rule`, `list-mobile-device-access-rules`, `update-mobile-device-access-rule`, `delete-mobile-device-access-rule`, `get-mobile-device-access-effect`, `put-mobile-device-access-override`, `get-mobile-device-access-override`, `delete-mobile-device-access-override`, `list-mobile-device-access-overrides` |
| Availability | [availability.md](availability.md) | `create-availability-configuration`, `list-availability-configurations`, `update-availability-configuration`, `delete-availability-configuration`, `test-availability-configuration` |
| Monitoring & Policies | [monitoring-policies.md](monitoring-policies.md) | `put-email-monitoring-configuration`, `describe-email-monitoring-configuration`, `delete-email-monitoring-configuration`, `put-retention-policy`, `get-default-retention-policy`, `delete-retention-policy` |
| Identity & Auth | [identity-auth.md](identity-auth.md) | `create-identity-center-application`, `delete-identity-center-application`, `put-identity-provider-configuration`, `describe-identity-provider-configuration`, `delete-identity-provider-configuration`, `get-personal-access-token-metadata`, `list-personal-access-tokens`, `delete-personal-access-token` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
| Message Flow | [message-flow.md](message-flow.md) | `get-raw-message-content`, `put-raw-message-content` |
