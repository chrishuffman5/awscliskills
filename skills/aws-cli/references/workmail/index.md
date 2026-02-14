# WorkMail — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `associate-delegate-to-resource` | Associate a delegate to a resource |
| `associate-member-to-group` | Associate a member to a group |
| `assume-impersonation-role` | Assume an impersonation role and get a token |
| `cancel-mailbox-export-job` | Cancel a mailbox export job |
| `create-alias` | Create an alias for a user or group |
| `create-availability-configuration` | Create an availability provider configuration |
| `create-group` | Create a group |
| `create-identity-center-application` | Create an Identity Center application for WorkMail |
| `create-impersonation-role` | Create an impersonation role |
| `create-mobile-device-access-rule` | Create a mobile device access rule |
| `create-organization` | Create a new WorkMail organization |
| `create-resource` | Create a room or equipment resource |
| `create-user` | Create a user |
| `delete-access-control-rule` | Delete an access control rule |
| `delete-alias` | Delete an alias |
| `delete-availability-configuration` | Delete an availability configuration |
| `delete-email-monitoring-configuration` | Delete email monitoring configuration |
| `delete-group` | Delete a group |
| `delete-identity-center-application` | Delete an Identity Center application |
| `delete-identity-provider-configuration` | Delete identity provider configuration |
| `delete-impersonation-role` | Delete an impersonation role |
| `delete-mailbox-permissions` | Delete mailbox permissions |
| `delete-mobile-device-access-override` | Delete a mobile device access override |
| `delete-mobile-device-access-rule` | Delete a mobile device access rule |
| `delete-organization` | Delete a WorkMail organization |
| `delete-personal-access-token` | Delete a personal access token |
| `delete-resource` | Delete a resource |
| `delete-retention-policy` | Delete a retention policy |
| `delete-user` | Delete a user |
| `deregister-from-work-mail` | Deregister an entity from WorkMail |
| `deregister-mail-domain` | Deregister a mail domain |
| `describe-email-monitoring-configuration` | Describe email monitoring configuration |
| `describe-entity` | Describe an entity (user, group, or resource) |
| `describe-group` | Describe a group |
| `describe-identity-provider-configuration` | Describe identity provider configuration |
| `describe-inbound-dmarc-settings` | Describe inbound DMARC settings |
| `describe-mailbox-export-job` | Describe a mailbox export job |
| `describe-organization` | Describe a WorkMail organization |
| `describe-resource` | Describe a resource |
| `describe-user` | Describe a user |
| `disassociate-delegate-from-resource` | Disassociate a delegate from a resource |
| `disassociate-member-from-group` | Disassociate a member from a group |
| `get-access-control-effect` | Get the access control effect for a given context |
| `get-default-retention-policy` | Get the default retention policy |
| `get-impersonation-role` | Get an impersonation role |
| `get-impersonation-role-effect` | Get the effect of an impersonation role for a user |
| `get-mail-domain` | Get mail domain details including DNS records |
| `get-mailbox-details` | Get mailbox size and quota details |
| `get-mobile-device-access-effect` | Get mobile device access effect for a device |
| `get-mobile-device-access-override` | Get a mobile device access override |
| `get-personal-access-token-metadata` | Get personal access token metadata |
| `list-access-control-rules` | List access control rules |
| `list-aliases` | List aliases for an entity |
| `list-availability-configurations` | List availability configurations |
| `list-group-members` | List members of a group |
| `list-groups` | List groups |
| `list-groups-for-entity` | List groups an entity belongs to |
| `list-impersonation-roles` | List impersonation roles |
| `list-mail-domains` | List mail domains |
| `list-mailbox-export-jobs` | List mailbox export jobs |
| `list-mailbox-permissions` | List mailbox permissions |
| `list-mobile-device-access-overrides` | List mobile device access overrides |
| `list-mobile-device-access-rules` | List mobile device access rules |
| `list-organizations` | List WorkMail organizations |
| `list-personal-access-tokens` | List personal access tokens |
| `list-resource-delegates` | List delegates for a resource |
| `list-resources` | List resources |
| `list-tags-for-resource` | List tags for a resource |
| `list-users` | List users |
| `put-access-control-rule` | Create or update an access control rule |
| `put-email-monitoring-configuration` | Set email monitoring configuration |
| `put-identity-provider-configuration` | Set identity provider configuration |
| `put-inbound-dmarc-settings` | Set inbound DMARC enforcement settings |
| `put-mailbox-permissions` | Set mailbox permissions |
| `put-mobile-device-access-override` | Set a mobile device access override |
| `put-retention-policy` | Create or update a retention policy |
| `register-mail-domain` | Register a mail domain with WorkMail |
| `register-to-work-mail` | Register an entity for WorkMail email |
| `reset-password` | Reset a user password |
| `start-mailbox-export-job` | Start a mailbox export job to S3 |
| `tag-resource` | Add tags to a resource |
| `test-availability-configuration` | Test an availability configuration |
| `untag-resource` | Remove tags from a resource |
| `update-availability-configuration` | Update an availability configuration |
| `update-default-mail-domain` | Update the default mail domain |
| `update-group` | Update a group |
| `update-impersonation-role` | Update an impersonation role |
| `update-mailbox-quota` | Update mailbox quota |
| `update-mobile-device-access-rule` | Update a mobile device access rule |
| `update-primary-email-address` | Update the primary email address |
| `update-resource` | Update a resource |
| `update-user` | Update a user |
| **workmailmessageflow** | |
| `get-raw-message-content` | Get raw email message content in MIME format |
| `put-raw-message-content` | Update raw email message content from S3 |

## Global Options

All commands accept these options:

| Option | Description |
|--------|-------------|
| `--output` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | JMESPath query to filter output |
| `--region` | AWS region |
| `--profile` | Named credential profile |
| `--no-cli-pager` | Disable pager for output |
| `--cli-input-json` | Read parameters from JSON string |
| `--cli-input-yaml` | Read parameters from YAML string |
| `--generate-cli-skeleton` | Print JSON/YAML input skeleton |

## Common Patterns

### List all enabled users in an organization
```bash
aws workmail list-users \
    --organization-id m-d281d0a2fd824be5b6cd3d3ce909fd27 \
    --filters State=ENABLED \
    --query 'Users[].{Name:Name,Email:Email,Role:UserRole}'
```

### Check mail domain DNS verification status
```bash
aws workmail get-mail-domain \
    --organization-id m-d281d0a2fd824be5b6cd3d3ce909fd27 \
    --domain-name example.com \
    --query '{Ownership:OwnershipVerificationStatus,DKIM:DkimVerificationStatus}'
```

### Get mailbox usage for a user
```bash
aws workmail get-mailbox-details \
    --organization-id m-d281d0a2fd824be5b6cd3d3ce909fd27 \
    --user-id jsmith \
    --query '{QuotaMB:MailboxQuota,UsedMB:MailboxSize}'
```
