# Remote Access

### 6.1 `create-remote-access-session`

Creates a remote access session, which provides the URL and credentials for interactive device access.

**Synopsis:**
```bash
aws devicefarm create-remote-access-session \
    --project-arn <value> \
    --device-arn <value> \
    [--instance-arn <value>] \
    [--ssh-public-key <value>] \
    [--remote-debug-enabled | --no-remote-debug-enabled] \
    [--remote-record-enabled | --no-remote-record-enabled] \
    [--remote-record-app-arn <value>] \
    [--name <value>] \
    [--client-id <value>] \
    [--configuration <value>] \
    [--interaction-mode <value>] \
    [--skip-app-resign | --no-skip-app-resign] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the project |
| `--device-arn` | **Yes** | string | -- | ARN of the device |
| `--instance-arn` | No | string | None | ARN of a specific device instance |
| `--ssh-public-key` | No | string | None | SSH public key for remote debug |
| `--remote-debug-enabled` | No | boolean | false | Enable remote debugging |
| `--remote-record-enabled` | No | boolean | false | Enable remote recording |
| `--remote-record-app-arn` | No | string | None | ARN of the app to record |
| `--name` | No | string | None | Name of the session |
| `--client-id` | No | string | None | Client ID for idempotency |
| `--configuration` | No | structure | None | Session configuration. Shorthand: `billingMethod=METERED\|UNMETERED,vpceConfigurationArns=string,string` |
| `--interaction-mode` | No | string | None | Interaction mode: `INTERACTIVE`, `NO_VIDEO`, `VIDEO_ONLY` |
| `--skip-app-resign` | No | boolean | false | Skip iOS app re-signing |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "remoteAccessSession": {
        "arn": "string",
        "name": "string",
        "created": "timestamp",
        "status": "PENDING|PENDING_CONCURRENCY|PENDING_DEVICE|PROCESSING|SCHEDULING|PREPARING|RUNNING|COMPLETED|STOPPING",
        "result": "PENDING|PASSED|WARNED|FAILED|SKIPPED|ERRORED|STOPPED",
        "message": "string",
        "started": "timestamp",
        "stopped": "timestamp",
        "device": {
            "arn": "string",
            "name": "string",
            "manufacturer": "string",
            "model": "string",
            "platform": "ANDROID|IOS",
            "os": "string",
            "formFactor": "PHONE|TABLET"
        },
        "instanceArn": "string",
        "remoteDebugEnabled": "boolean",
        "remoteRecordEnabled": "boolean",
        "remoteRecordAppArn": "string",
        "hostAddress": "string",
        "clientId": "string",
        "billingMethod": "METERED|UNMETERED",
        "deviceMinutes": {
            "total": "double",
            "metered": "double",
            "unmetered": "double"
        },
        "endpoint": "string",
        "deviceUdid": "string",
        "interactionMode": "INTERACTIVE|NO_VIDEO|VIDEO_ONLY",
        "skipAppResign": "boolean",
        "vpcConfig": {}
    }
}
```

---

### 6.2 `delete-remote-access-session`

Deletes a completed remote access session and its results.

**Synopsis:**
```bash
aws devicefarm delete-remote-access-session \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the remote access session to delete |

**Output Schema:**
```json
{}
```

---

### 6.3 `get-remote-access-session`

Returns a remote access session.

**Synopsis:**
```bash
aws devicefarm get-remote-access-session \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the remote access session |

**Output Schema:**
```json
{
    "remoteAccessSession": {
        "arn": "string",
        "name": "string",
        "created": "timestamp",
        "status": "PENDING|PENDING_CONCURRENCY|PENDING_DEVICE|PROCESSING|SCHEDULING|PREPARING|RUNNING|COMPLETED|STOPPING",
        "result": "PENDING|PASSED|WARNED|FAILED|SKIPPED|ERRORED|STOPPED",
        "message": "string",
        "started": "timestamp",
        "stopped": "timestamp",
        "device": {
            "arn": "string",
            "name": "string",
            "manufacturer": "string",
            "model": "string",
            "platform": "ANDROID|IOS",
            "os": "string"
        },
        "remoteDebugEnabled": "boolean",
        "remoteRecordEnabled": "boolean",
        "hostAddress": "string",
        "clientId": "string",
        "billingMethod": "METERED|UNMETERED",
        "deviceMinutes": {},
        "endpoint": "string",
        "interactionMode": "INTERACTIVE|NO_VIDEO|VIDEO_ONLY",
        "skipAppResign": "boolean"
    }
}
```

---

### 6.4 `list-remote-access-sessions`

Returns a list of all remote access sessions for a project. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-remote-access-sessions \
    --arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the project |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "remoteAccessSessions": [
        {
            "arn": "string",
            "name": "string",
            "created": "timestamp",
            "status": "string",
            "result": "string",
            "started": "timestamp",
            "stopped": "timestamp",
            "device": {},
            "billingMethod": "METERED|UNMETERED",
            "deviceMinutes": {},
            "endpoint": "string",
            "interactionMode": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.5 `stop-remote-access-session`

Ends a specified remote access session.

**Synopsis:**
```bash
aws devicefarm stop-remote-access-session \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the remote access session to stop |

**Output Schema:**
```json
{
    "remoteAccessSession": {
        "arn": "string",
        "name": "string",
        "created": "timestamp",
        "status": "STOPPING|COMPLETED",
        "result": "string",
        "started": "timestamp",
        "stopped": "timestamp",
        "device": {},
        "billingMethod": "METERED|UNMETERED",
        "deviceMinutes": {},
        "endpoint": "string"
    }
}
```
