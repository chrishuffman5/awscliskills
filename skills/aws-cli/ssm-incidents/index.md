# AWS CLI v2 -- SSM Incidents + SSM Contacts Command Reference Index

> Based on AWS CLI v2 documentation.
> Sources: https://docs.aws.amazon.com/cli/latest/reference/ssm-incidents/ and https://docs.aws.amazon.com/cli/latest/reference/ssm-contacts/

---

## Quick Reference

| Command | Service | Category | Description |
|---------|---------|----------|-------------|
| `create-response-plan` | ssm-incidents | Response Plan | Create a response plan |
| `delete-response-plan` | ssm-incidents | Response Plan | Delete a response plan |
| `get-response-plan` | ssm-incidents | Response Plan | Get a response plan |
| `list-response-plans` | ssm-incidents | Response Plan | List response plans |
| `update-response-plan` | ssm-incidents | Response Plan | Update a response plan |
| `start-incident` | ssm-incidents | Incident | Start an incident |
| `get-incident-record` | ssm-incidents | Incident | Get an incident record |
| `delete-incident-record` | ssm-incidents | Incident | Delete an incident record |
| `update-incident-record` | ssm-incidents | Incident | Update an incident record |
| `list-incident-records` | ssm-incidents | Incident | List incident records |
| `update-deletion-protection` | ssm-incidents | Incident | Update deletion protection |
| `batch-get-incident-findings` | ssm-incidents | Incident Finding | Batch get incident findings |
| `list-incident-findings` | ssm-incidents | Incident Finding | List incident findings |
| `list-related-items` | ssm-incidents | Related Item | List related items for an incident |
| `update-related-items` | ssm-incidents | Related Item | Update related items |
| `create-timeline-event` | ssm-incidents | Timeline Event | Create a timeline event |
| `delete-timeline-event` | ssm-incidents | Timeline Event | Delete a timeline event |
| `get-timeline-event` | ssm-incidents | Timeline Event | Get a timeline event |
| `list-timeline-events` | ssm-incidents | Timeline Event | List timeline events |
| `update-timeline-event` | ssm-incidents | Timeline Event | Update a timeline event |
| `create-replication-set` | ssm-incidents | Replication Set | Create a replication set |
| `delete-replication-set` | ssm-incidents | Replication Set | Delete a replication set |
| `get-replication-set` | ssm-incidents | Replication Set | Get a replication set |
| `list-replication-sets` | ssm-incidents | Replication Set | List replication sets |
| `update-replication-set` | ssm-incidents | Replication Set | Update a replication set |
| `get-resource-policies` | ssm-incidents | Resource Policy | Get resource policies |
| `put-resource-policy` | ssm-incidents | Resource Policy | Put a resource policy |
| `delete-resource-policy` | ssm-incidents | Resource Policy | Delete a resource policy |
| `create-contact` | ssm-contacts | Contact | Create a contact |
| `delete-contact` | ssm-contacts | Contact | Delete a contact |
| `get-contact` | ssm-contacts | Contact | Get a contact |
| `list-contacts` | ssm-contacts | Contact | List contacts |
| `update-contact` | ssm-contacts | Contact | Update a contact |
| `get-contact-policy` | ssm-contacts | Contact | Get a contact policy |
| `put-contact-policy` | ssm-contacts | Contact | Put a contact policy |
| `create-contact-channel` | ssm-contacts | Contact Channel | Create a contact channel |
| `delete-contact-channel` | ssm-contacts | Contact Channel | Delete a contact channel |
| `get-contact-channel` | ssm-contacts | Contact Channel | Get a contact channel |
| `list-contact-channels` | ssm-contacts | Contact Channel | List contact channels |
| `update-contact-channel` | ssm-contacts | Contact Channel | Update a contact channel |
| `activate-contact-channel` | ssm-contacts | Contact Channel | Activate a contact channel |
| `deactivate-contact-channel` | ssm-contacts | Contact Channel | Deactivate a contact channel |
| `send-activation-code` | ssm-contacts | Contact Channel | Send an activation code |
| `start-engagement` | ssm-contacts | Engagement | Start an engagement |
| `stop-engagement` | ssm-contacts | Engagement | Stop an engagement |
| `describe-engagement` | ssm-contacts | Engagement | Describe an engagement |
| `list-engagements` | ssm-contacts | Engagement | List engagements |
| `accept-page` | ssm-contacts | Engagement | Accept a page |
| `describe-page` | ssm-contacts | Engagement | Describe a page |
| `list-pages-by-contact` | ssm-contacts | Engagement | List pages for a contact |
| `list-pages-by-engagement` | ssm-contacts | Engagement | List pages for an engagement |
| `list-page-receipts` | ssm-contacts | Engagement | List page receipts |
| `list-page-resolutions` | ssm-contacts | Engagement | List page resolutions |
| `create-rotation` | ssm-contacts | Rotation | Create a rotation |
| `delete-rotation` | ssm-contacts | Rotation | Delete a rotation |
| `get-rotation` | ssm-contacts | Rotation | Get a rotation |
| `list-rotations` | ssm-contacts | Rotation | List rotations |
| `update-rotation` | ssm-contacts | Rotation | Update a rotation |
| `create-rotation-override` | ssm-contacts | Rotation | Create a rotation override |
| `delete-rotation-override` | ssm-contacts | Rotation | Delete a rotation override |
| `get-rotation-override` | ssm-contacts | Rotation | Get a rotation override |
| `list-rotation-overrides` | ssm-contacts | Rotation | List rotation overrides |
| `list-rotation-shifts` | ssm-contacts | Rotation | List rotation shifts |
| `list-preview-rotation-shifts` | ssm-contacts | Rotation | Preview rotation shifts |
| `tag-resource` | both | Tags | Add tags to a resource |
| `untag-resource` | both | Tags | Remove tags from a resource |
| `list-tags-for-resource` | both | Tags | List tags for a resource |
| `wait replication-set-active` | ssm-incidents | Wait | Wait until replication set is active |
| `wait replication-set-deleted` | ssm-incidents | Wait | Wait until replication set is deleted |

---

## Global Options

These options are available on ALL `aws ssm-incidents` and `aws ssm-contacts` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Incident Impact Levels
| Impact | Description |
|--------|-------------|
| `1` | Critical impact |
| `2` | High impact |
| `3` | Medium impact |
| `4` | Low impact |
| `5` | No impact |

### Incident Record Status Values
| Status | Description |
|--------|-------------|
| `OPEN` | Incident is active |
| `RESOLVED` | Incident has been resolved |

### Contact Types
| Type | Description |
|------|-------------|
| `PERSONAL` | A single person contact |
| `ESCALATION` | An escalation plan |
| `ONCALL_SCHEDULE` | An on-call schedule |

### Contact Channel Types
| Type | Description |
|------|-------------|
| `SMS` | SMS message |
| `VOICE` | Voice call |
| `EMAIL` | Email message |

### Replication Set Status Values
| Status | Description |
|--------|-------------|
| `ACTIVE` | Replication set is active |
| `CREATING` | Replication set is being created |
| `UPDATING` | Replication set is being updated |
| `DELETING` | Replication set is being deleted |
| `FAILED` | Replication set creation/update failed |

### Day of Week Values (Rotations)
`MON`, `TUE`, `WED`, `THU`, `FRI`, `SAT`, `SUN`
