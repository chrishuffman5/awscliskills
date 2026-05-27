# Pools

### 6.1 `create-workspaces-pool`

Creates a pool of WorkSpaces. A pool allows multiple users to share a set of WorkSpaces.

**Synopsis:**
```bash
aws workspaces create-workspaces-pool \
    --pool-name <value> \
    --description <value> \
    --bundle-id <value> \
    --directory-id <value> \
    --capacity <value> \
    [--application-settings <value>] \
    [--timeout-settings <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-name` | **Yes** | string | -- | The name of the pool |
| `--description` | **Yes** | string | -- | The description of the pool |
| `--bundle-id` | **Yes** | string | -- | The bundle ID for the pool |
| `--directory-id` | **Yes** | string | -- | The directory ID for the pool |
| `--capacity` | **Yes** | structure | -- | Pool capacity. Shorthand: `DesiredUserSessions=integer` |
| `--application-settings` | No | structure | None | Application settings (persistent app settings). Shorthand: `Status=ENABLED\|DISABLED,SettingsGroup=string` |
| `--timeout-settings` | No | structure | None | Timeout settings. Shorthand: `DisconnectTimeoutInSeconds=integer,IdleDisconnectTimeoutInSeconds=integer,MaxUserDurationInSeconds=integer` |
| `--tags` | No | list | None | Tags to associate. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "WorkspacesPool": {
        "PoolId": "string",
        "PoolArn": "string",
        "CapacityStatus": {
            "AvailableUserSessions": "integer",
            "DesiredUserSessions": "integer",
            "ActualUserSessions": "integer",
            "ActiveUserSessions": "integer"
        },
        "PoolName": "string",
        "Description": "string",
        "State": "CREATING|DELETING|RUNNING|STARTING|STOPPED|STOPPING|UPDATING",
        "CreatedAt": "timestamp",
        "BundleId": "string",
        "DirectoryId": "string",
        "Errors": [
            {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        ],
        "ApplicationSettings": {
            "Status": "ENABLED|DISABLED",
            "SettingsGroup": "string",
            "S3BucketName": "string"
        },
        "TimeoutSettings": {
            "DisconnectTimeoutInSeconds": "integer",
            "IdleDisconnectTimeoutInSeconds": "integer",
            "MaxUserDurationInSeconds": "integer"
        }
    }
}
```

---

### 6.2 `terminate-workspaces-pool`

Terminates the specified WorkSpaces pool.

**Synopsis:**
```bash
aws workspaces terminate-workspaces-pool \
    --pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-id` | **Yes** | string | -- | The pool ID to terminate |

**Output Schema:**
```json
{}
```

---

### 6.3 `describe-workspaces-pools`

Describes the specified WorkSpaces pools or all pools. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces describe-workspaces-pools \
    [--pool-ids <value>] \
    [--filters <value>] \
    [--limit <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-ids` | No | list(string) | None | One or more pool IDs |
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string,Operator=EQUALS` |
| `--limit` | No | integer | None | Maximum number of items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "WorkspacesPools": [
        {
            "PoolId": "string",
            "PoolArn": "string",
            "CapacityStatus": {
                "AvailableUserSessions": "integer",
                "DesiredUserSessions": "integer",
                "ActualUserSessions": "integer",
                "ActiveUserSessions": "integer"
            },
            "PoolName": "string",
            "Description": "string",
            "State": "CREATING|DELETING|RUNNING|STARTING|STOPPED|STOPPING|UPDATING",
            "CreatedAt": "timestamp",
            "BundleId": "string",
            "DirectoryId": "string",
            "Errors": [],
            "ApplicationSettings": {},
            "TimeoutSettings": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `update-workspaces-pool`

Updates the specified WorkSpaces pool.

**Synopsis:**
```bash
aws workspaces update-workspaces-pool \
    --pool-id <value> \
    [--description <value>] \
    [--bundle-id <value>] \
    [--directory-id <value>] \
    [--capacity <value>] \
    [--application-settings <value>] \
    [--timeout-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-id` | **Yes** | string | -- | The pool ID to update |
| `--description` | No | string | None | New description |
| `--bundle-id` | No | string | None | New bundle ID |
| `--directory-id` | No | string | None | New directory ID |
| `--capacity` | No | structure | None | Updated capacity. Shorthand: `DesiredUserSessions=integer` |
| `--application-settings` | No | structure | None | Updated application settings |
| `--timeout-settings` | No | structure | None | Updated timeout settings |

**Output Schema:**
```json
{
    "WorkspacesPool": {
        "PoolId": "string",
        "PoolArn": "string",
        "CapacityStatus": {
            "AvailableUserSessions": "integer",
            "DesiredUserSessions": "integer",
            "ActualUserSessions": "integer",
            "ActiveUserSessions": "integer"
        },
        "PoolName": "string",
        "Description": "string",
        "State": "CREATING|DELETING|RUNNING|STARTING|STOPPED|STOPPING|UPDATING",
        "CreatedAt": "timestamp",
        "BundleId": "string",
        "DirectoryId": "string",
        "Errors": [],
        "ApplicationSettings": {},
        "TimeoutSettings": {}
    }
}
```

---

### 6.5 `start-workspaces-pool`

Starts the specified WorkSpaces pool.

**Synopsis:**
```bash
aws workspaces start-workspaces-pool \
    --pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-id` | **Yes** | string | -- | The pool ID to start |

**Output Schema:**
```json
{}
```

---

### 6.6 `stop-workspaces-pool`

Stops the specified WorkSpaces pool.

**Synopsis:**
```bash
aws workspaces stop-workspaces-pool \
    --pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-id` | **Yes** | string | -- | The pool ID to stop |

**Output Schema:**
```json
{}
```

---

### 6.7 `describe-workspaces-pool-sessions`

Describes the sessions for a WorkSpaces pool. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces describe-workspaces-pool-sessions \
    --pool-id <value> \
    [--user-id <value>] \
    [--limit <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-id` | **Yes** | string | -- | The pool ID |
| `--user-id` | No | string | None | Filter by user ID |
| `--limit` | No | integer | None | Maximum number of items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Sessions": [
        {
            "AuthenticationType": "SAML|CERTIFICATE",
            "ConnectionState": "CONNECTED|NOT_CONNECTED",
            "SessionId": "string",
            "PoolId": "string",
            "UserId": "string",
            "WorkspaceId": "string",
            "InstanceId": "string",
            "StartTime": "timestamp",
            "ExpirationTime": "timestamp",
            "NetworkAccessConfiguration": {
                "EniPrivateIpAddress": "string",
                "EniId": "string"
            }
        }
    ],
    "NextToken": "string"
}
```
