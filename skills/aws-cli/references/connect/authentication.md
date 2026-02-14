# Authentication

### 25.1 `describe-authentication-profile`

Describes an authentication profile.

**Synopsis:**
```bash
aws connect describe-authentication-profile \
    --authentication-profile-id <value> \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authentication-profile-id` | **Yes** | string | -- | Authentication profile ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output Schema:**
```json
{
    "AuthenticationProfile": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "AllowedIps": ["string"],
        "BlockedIps": ["string"],
        "IsDefault": "boolean",
        "CreatedTime": "timestamp",
        "LastModifiedTime": "timestamp",
        "LastModifiedRegion": "string",
        "PeriodicSessionDuration": "integer",
        "MaxSessionDuration": "integer"
    }
}
```

---

### 25.2 `list-authentication-profiles`

Lists authentication profiles. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-25) |

**Output Schema:**
```json
{
    "AuthenticationProfileSummaryList": [ { "Id": "string", "Arn": "string", "Name": "string", "IsDefault": "boolean", "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" } ],
    "NextToken": "string"
}
```

---

### 25.3 `update-authentication-profile`

Updates an authentication profile.

**Synopsis:**
```bash
aws connect update-authentication-profile \
    --authentication-profile-id <value> \
    --instance-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--allowed-ips <value>] \
    [--blocked-ips <value>] \
    [--periodic-session-duration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authentication-profile-id` | **Yes** | string | -- | Authentication profile ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--allowed-ips` | No | list | None | Allowed IP ranges (CIDR) |
| `--blocked-ips` | No | list | None | Blocked IP ranges (CIDR) |
| `--periodic-session-duration` | No | integer | None | Session duration in minutes |

**Output:** None

---

### 25.4 `update-participant-authentication`

Updates participant authentication for a contact.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--state` | **Yes** | string | -- | Authentication state |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output Schema:**
```json
{
    "Output": {}
}
```
