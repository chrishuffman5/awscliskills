# AWS CLI v2 -- STS (Security Token Service) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/sts/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `assume-role` | Assume Role | Assume an IAM role and get temporary credentials |
| `assume-role-with-saml` | Assume Role | Assume a role using a SAML authentication response |
| `assume-role-with-web-identity` | Assume Role | Assume a role using an OIDC/web identity token |
| `get-session-token` | Credentials | Get temporary credentials for an IAM user (supports MFA) |
| `get-federation-token` | Credentials | Get temporary credentials for a federated user |
| `get-access-key-info` | Credentials | Get the account ID associated with an access key |
| `get-caller-identity` | Identity | Get the identity of the calling entity |
| `decode-authorization-message` | Identity | Decode an encoded authorization failure message |

---

## Global Options

These options are available on ALL `aws sts` commands.

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

### Temporary Credentials Structure
All STS operations that return credentials use this structure:
```json
{
    "AccessKeyId": "string",
    "SecretAccessKey": "string",
    "SessionToken": "string",
    "Expiration": "timestamp"
}
```

### Session Duration Limits

| Operation | Min | Default | Max (Role) | Max (User/Root) |
|-----------|-----|---------|------------|-----------------|
| `assume-role` | 900s (15m) | 3600s (1h) | 43200s (12h)* | -- |
| `assume-role-with-saml` | 900s (15m) | 3600s (1h) | 43200s (12h)* | -- |
| `assume-role-with-web-identity` | 900s (15m) | 3600s (1h) | 43200s (12h)* | -- |
| `get-session-token` | 900s (15m) | 43200s (12h) | -- | 129600s (36h) |
| `get-federation-token` | 900s (15m) | 43200s (12h) | -- | 129600s (36h) |

*Maximum depends on role's `MaxSessionDuration` setting.

### STS Regional Endpoints
STS supports regional endpoints for lower latency:
```bash
aws sts get-caller-identity --region us-west-2 --endpoint-url https://sts.us-west-2.amazonaws.com
```

### Policy Constraints
- **PolicyArns**: Maximum 10 managed policy ARNs per call
- **Policy**: Inline session policy JSON, max 2048 characters (packed)
- Combined policy size (all session policies): max 2048 characters after packing
