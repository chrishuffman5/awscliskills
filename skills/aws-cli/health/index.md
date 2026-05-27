# AWS CLI v2 -- AWS Health Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/health/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `describe-events` | Event | List Health events with optional filters (paginated) |
| `describe-event-details` | Event | Get detailed information about Health events (batch, up to 10) |
| `describe-event-types` | Event | List available Health event types (paginated) |
| `describe-event-aggregates` | Event | Get aggregate counts of Health events by category |
| `describe-affected-entities` | Affected Entity | List entities (resources) affected by a Health event (paginated) |
| `describe-entity-aggregates` | Affected Entity | Get aggregate entity counts for specified events |
| `describe-events-for-organization` | Organization | List Health events across the organization (paginated) |
| `describe-event-details-for-organization` | Organization | Get event details across the organization (batch, up to 10) |
| `describe-affected-entities-for-organization` | Organization | List affected entities across the organization (paginated) |
| `describe-affected-accounts-for-organization` | Organization | List affected accounts for an org event (paginated) |
| `describe-entity-aggregates-for-organization` | Organization | Get entity aggregate counts across the organization |
| `enable-health-service-access-for-organization` | Organization Access | Enable Health organizational view |
| `disable-health-service-access-for-organization` | Organization Access | Disable Health organizational view |
| `describe-health-service-status-for-organization` | Organization Access | Check Health organizational view status |

---

## Global Options

These options are available on ALL `aws health` commands.

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

### Event Type Categories
| Category | Description |
|----------|-------------|
| `issue` | Service issue affecting your resources |
| `accountNotification` | Account-specific notification |
| `scheduledChange` | Planned change to your resources |
| `investigation` | Active investigation into an issue |

### Event Status Codes
| Status | Description |
|--------|-------------|
| `open` | Event is currently open |
| `closed` | Event has been resolved |
| `upcoming` | Event is scheduled for the future |

### Entity Status Codes
| Status | Description |
|--------|-------------|
| `IMPAIRED` | Entity is currently impaired |
| `UNIMPAIRED` | Entity is not affected |
| `UNKNOWN` | Entity status is unknown |
| `PENDING` | Status determination is pending |
| `RESOLVED` | Issue has been resolved |

### Event Scope Codes
| Scope | Description |
|-------|-------------|
| `PUBLIC` | Event is not account-specific |
| `ACCOUNT_SPECIFIC` | Event is specific to your account |
| `NONE` | No scope |

### Actionability
| Value | Description |
|-------|-------------|
| `ACTION_REQUIRED` | Action is required from you |
| `ACTION_MAY_BE_REQUIRED` | Action may be needed |
| `INFORMATIONAL` | For information only |

### Personas
| Value | Description |
|-------|-------------|
| `OPERATIONS` | Operations team |
| `SECURITY` | Security team |
| `BILLING` | Billing team |

### Region Requirement
Health API calls must be made to `us-east-1` for global events, or to the event's region for regional events.

### Support Plan Requirement
AWS Health API requires a Business, Enterprise On-Ramp, or Enterprise Support plan from AWS Support.
