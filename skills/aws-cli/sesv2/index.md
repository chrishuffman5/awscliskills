# AWS CLI v2 -- SES v2 (Simple Email Service v2) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/sesv2/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-email-identity` | Email Identity | Create an email identity (email address or domain) |
| `delete-email-identity` | Email Identity | Delete an email identity |
| `get-email-identity` | Email Identity | Get details about an email identity |
| `list-email-identities` | Email Identity | List all email identities |
| `put-email-identity-dkim-signing-attributes` | Email Identity | Configure DKIM signing for an identity |
| `put-email-identity-dkim-attributes` | Email Identity | Enable or disable DKIM for an identity |
| `put-email-identity-feedback-attributes` | Email Identity | Enable or disable feedback forwarding for an identity |
| `put-email-identity-mail-from-attributes` | Email Identity | Configure custom MAIL FROM domain |
| `put-email-identity-configuration-set-attributes` | Email Identity | Associate a configuration set with an identity |
| `create-configuration-set` | Configuration Set | Create a configuration set |
| `delete-configuration-set` | Configuration Set | Delete a configuration set |
| `get-configuration-set` | Configuration Set | Get details about a configuration set |
| `list-configuration-sets` | Configuration Set | List all configuration sets |
| `create-configuration-set-event-destination` | Configuration Set | Create an event destination for a configuration set |
| `delete-configuration-set-event-destination` | Configuration Set | Delete an event destination |
| `get-configuration-set-event-destinations` | Configuration Set | List event destinations for a configuration set |
| `update-configuration-set-event-destination` | Configuration Set | Update an event destination |
| `create-contact-list` | Contact List | Create a contact list |
| `delete-contact-list` | Contact List | Delete a contact list |
| `get-contact-list` | Contact List | Get details about a contact list |
| `list-contact-lists` | Contact List | List all contact lists |
| `update-contact-list` | Contact List | Update a contact list |
| `create-contact` | Contact | Create a contact in a contact list |
| `delete-contact` | Contact | Delete a contact from a contact list |
| `get-contact` | Contact | Get details about a contact |
| `list-contacts` | Contact | List contacts in a contact list |
| `update-contact` | Contact | Update a contact |
| `create-email-template` | Email Template | Create an email template |
| `delete-email-template` | Email Template | Delete an email template |
| `get-email-template` | Email Template | Get details about an email template |
| `list-email-templates` | Email Template | List all email templates |
| `update-email-template` | Email Template | Update an email template |
| `send-email` | Sending | Send an email message |
| `send-bulk-email` | Sending | Send bulk templated emails |
| `create-email-identity-policy` | Sending | Create a sending authorization policy |
| `delete-email-identity-policy` | Sending | Delete a sending authorization policy |
| `get-email-identity-policies` | Sending | Get sending authorization policies |
| `put-suppressed-destination` | Suppression | Add an email address to the suppression list |
| `get-suppressed-destination` | Suppression | Get details about a suppressed destination |
| `delete-suppressed-destination` | Suppression | Remove an email address from the suppression list |
| `list-suppressed-destinations` | Suppression | List suppressed destinations |
| `put-account-suppression-attributes` | Suppression | Configure account-level suppression |
| `get-dedicated-ip` | Dedicated IP | Get info about a specific dedicated IP |
| `get-dedicated-ips` | Dedicated IP | List dedicated IPs for the account |
| `list-dedicated-ip-pools` | Dedicated IP | List dedicated IP pools |
| `create-dedicated-ip-pool` | Dedicated IP | Create a dedicated IP pool |
| `delete-dedicated-ip-pool` | Dedicated IP | Delete a dedicated IP pool |
| `put-dedicated-ip-in-pool` | Dedicated IP | Move a dedicated IP to a pool |
| `put-dedicated-ip-warmup-attributes` | Dedicated IP | Set warmup percentage for a dedicated IP |
| `get-account` | Account | Get account details and sending limits |
| `put-account-details` | Account | Update account details |
| `put-account-sending-attributes` | Account | Enable or disable email sending |
| `put-account-dedicated-ip-warmup-attributes` | Account | Configure dedicated IP warmup behavior |
| `get-deliverability-dashboard-options` | Account | Get deliverability dashboard status |
| `put-deliverability-dashboard-option` | Account | Enable or disable the deliverability dashboard |

---

## Global Options

These options are available on ALL `aws sesv2` commands.

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

### Identity Types
| Type | Example | Description |
|------|---------|-------------|
| Email Address | `user@example.com` | Individual email address identity |
| Domain | `example.com` | Domain-level identity (covers all addresses) |

### DKIM Signing Key Types
| Type | Description |
|------|-------------|
| `RSA_1024_BIT` | 1024-bit RSA key (Easy DKIM) |
| `RSA_2048_BIT` | 2048-bit RSA key (Easy DKIM) |
| `ED25519` | Ed25519 key (BYO DKIM) |

### Suppression Reasons
| Reason | Description |
|--------|-------------|
| `BOUNCE` | Hard bounce occurred |
| `COMPLAINT` | Recipient complained |

### Event Types
| Event | Description |
|-------|-------------|
| `SEND` | Message was sent |
| `REJECT` | Message was rejected |
| `BOUNCE` | Hard bounce occurred |
| `COMPLAINT` | Complaint received |
| `DELIVERY` | Message was delivered |
| `OPEN` | Message was opened |
| `CLICK` | Link was clicked |
| `RENDERING_FAILURE` | Template rendering failed |
| `DELIVERY_DELAY` | Delivery was delayed |
| `SUBSCRIPTION` | Subscription event |

### Mail From Behavior on MX Failure
| Behavior | Description |
|----------|-------------|
| `USE_DEFAULT_VALUE` | Use default amazonses.com MAIL FROM |
| `REJECT_MESSAGE` | Return a bounce response |
