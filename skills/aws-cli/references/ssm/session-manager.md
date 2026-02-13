# Session Manager

### 4.1 `start-session`

Starts a Session Manager session with a managed instance. Requires the Session Manager plugin for the AWS CLI.

**Synopsis:**
```bash
aws ssm start-session \
    --target <value> \
    [--document-name <value>] \
    [--parameters <value>] \
    [--reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target` | **Yes** | string | -- | Instance ID to connect to |
| `--document-name` | No | string | `SSM-SessionManagerRunShell` | Session document to use |
| `--parameters` | No | map | None | Session document parameters |
| `--reason` | No | string | None | Reason for starting the session |

**Output Schema:**
```json
{
    "SessionId": "string",
    "TokenValue": "string",
    "StreamUrl": "string"
}
```

---

### 4.2 `terminate-session`

Terminates an active Session Manager session.

**Synopsis:**
```bash
aws ssm terminate-session \
    --session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID to terminate |

**Output Schema:**
```json
{
    "SessionId": "string"
}
```

---

### 4.3 `describe-sessions`

Lists Session Manager sessions. Supports filtering by status. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-sessions \
    --state <value> \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--state` | **Yes** | string | -- | Session state: `Active` or `History` |
| `--filters` | No | list | None | Filters: `InvokedAfter`, `InvokedBefore`, `Target`, `Owner`, `Status`, `SessionId` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Sessions": [
        {
            "SessionId": "string",
            "Target": "string",
            "Status": "Connected|Connecting|Disconnected|Terminated|Terminating|Failed",
            "StartDate": "timestamp",
            "EndDate": "timestamp",
            "DocumentName": "string",
            "Owner": "string",
            "Reason": "string",
            "Details": "string",
            "OutputUrl": {
                "S3OutputUrl": "string",
                "CloudWatchOutputUrl": "string"
            },
            "MaxSessionDuration": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `resume-session`

Reconnects to a disconnected Session Manager session.

**Synopsis:**
```bash
aws ssm resume-session \
    --session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID to resume |

**Output Schema:**
```json
{
    "SessionId": "string",
    "TokenValue": "string",
    "StreamUrl": "string"
}
```
