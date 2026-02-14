# App Instance Users

CLI namespace: `aws chime-sdk-identity`

### 2.1 `create-app-instance-user`

Creates an AppInstanceUser.

**Synopsis:**
```bash
aws chime-sdk-identity create-app-instance-user \
    --app-instance-arn <value> \
    --app-instance-user-id <value> \
    --name <value> \
    [--metadata <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--expiration-settings <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--app-instance-user-id` | **Yes** | string | -- | User ID (1-64 chars) |
| `--name` | **Yes** | string | -- | User display name (1-100 chars) |
| `--metadata` | No | string | None | Metadata (0-1024 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--tags` | No | list | None | Tags (1-50) |
| `--expiration-settings` | No | structure | None | Expiration settings |

**Output Schema:**
```json
{
    "AppInstanceUserArn": "string"
}
```

---

### 2.2 `describe-app-instance-user`

Describes an AppInstanceUser.

**Synopsis:**
```bash
aws chime-sdk-identity describe-app-instance-user \
    --app-instance-user-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-user-arn` | **Yes** | string | -- | User ARN |

**Output Schema:**
```json
{
    "AppInstanceUser": {
        "AppInstanceUserArn": "string",
        "Name": "string",
        "Metadata": "string",
        "CreatedTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp",
        "ExpirationSettings": {
            "ExpirationDays": "integer",
            "ExpirationCriterion": "CREATED_TIMESTAMP"
        }
    }
}
```

---

### 2.3 `list-app-instance-users`

Lists AppInstanceUsers. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-identity list-app-instance-users \
    --app-instance-arn <value> \
    [--max-results <value>] \
    [--next-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--max-results` | No | integer | None | Max results (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "AppInstanceArn": "string",
    "AppInstanceUsers": [
        {
            "AppInstanceUserArn": "string",
            "Name": "string",
            "Metadata": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `update-app-instance-user`

Updates an AppInstanceUser name and metadata.

**Synopsis:**
```bash
aws chime-sdk-identity update-app-instance-user \
    --app-instance-user-arn <value> \
    --name <value> \
    --metadata <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-user-arn` | **Yes** | string | -- | User ARN |
| `--name` | **Yes** | string | -- | Updated name (1-100 chars) |
| `--metadata` | **Yes** | string | -- | Updated metadata (0-1024 chars) |

**Output Schema:**
```json
{
    "AppInstanceUserArn": "string"
}
```

---

### 2.5 `delete-app-instance-user`

Deletes an AppInstanceUser.

**Synopsis:**
```bash
aws chime-sdk-identity delete-app-instance-user \
    --app-instance-user-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-user-arn` | **Yes** | string | -- | User ARN |

**Output:** None

---

### 2.6 `register-app-instance-user-endpoint`

Registers an endpoint under an AppInstanceUser for push notifications.

**Synopsis:**
```bash
aws chime-sdk-identity register-app-instance-user-endpoint \
    --app-instance-user-arn <value> \
    --type <value> \
    --resource-arn <value> \
    --endpoint-attributes <value> \
    [--name <value>] \
    [--allow-messages <value>] \
    [--client-request-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-user-arn` | **Yes** | string | -- | User ARN |
| `--type` | **Yes** | string | -- | `APNS`, `APNS_SANDBOX`, `GCM` |
| `--resource-arn` | **Yes** | string | -- | SNS platform application ARN |
| `--endpoint-attributes` | **Yes** | structure | -- | Device token in `DeviceToken` field |
| `--name` | No | string | None | Endpoint name (0-1600 chars) |
| `--allow-messages` | No | string | None | `ALL` or `NONE` |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "AppInstanceUserArn": "string",
    "EndpointId": "string"
}
```

---

### 2.7 `describe-app-instance-user-endpoint`

Describes an endpoint for an AppInstanceUser.

**Synopsis:**
```bash
aws chime-sdk-identity describe-app-instance-user-endpoint \
    --app-instance-user-arn <value> \
    --endpoint-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-user-arn` | **Yes** | string | -- | User ARN |
| `--endpoint-id` | **Yes** | string | -- | Endpoint ID (0-64 chars) |

**Output Schema:**
```json
{
    "AppInstanceUserEndpoint": {
        "AppInstanceUserArn": "string",
        "EndpointId": "string",
        "Name": "string",
        "Type": "APNS|APNS_SANDBOX|GCM",
        "ResourceArn": "string",
        "EndpointAttributes": {"DeviceToken": "string", "VoipDeviceToken": "string"},
        "CreatedTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp",
        "AllowMessages": "ALL|NONE",
        "EndpointState": {"Status": "ACTIVE|INACTIVE", "StatusReason": "string"}
    }
}
```

---

### 2.8 `list-app-instance-user-endpoints`

Lists endpoints for an AppInstanceUser. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-identity list-app-instance-user-endpoints \
    --app-instance-user-arn <value> \
    [--max-results <value>] \
    [--next-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-user-arn` | **Yes** | string | -- | User ARN |
| `--max-results` | No | integer | None | Max results (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "AppInstanceUserEndpoints": [
        {
            "AppInstanceUserArn": "string",
            "EndpointId": "string",
            "Name": "string",
            "Type": "APNS|APNS_SANDBOX|GCM",
            "AllowMessages": "ALL|NONE",
            "EndpointState": {"Status": "ACTIVE|INACTIVE"}
        }
    ],
    "NextToken": "string"
}
```

---

### 2.9 `deregister-app-instance-user-endpoint`

Deregisters an endpoint for an AppInstanceUser.

**Synopsis:**
```bash
aws chime-sdk-identity deregister-app-instance-user-endpoint \
    --app-instance-user-arn <value> \
    --endpoint-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-user-arn` | **Yes** | string | -- | User ARN |
| `--endpoint-id` | **Yes** | string | -- | Endpoint ID |

**Output:** None

---

### 2.10 `update-app-instance-user-endpoint`

Updates an endpoint for an AppInstanceUser.

**Synopsis:**
```bash
aws chime-sdk-identity update-app-instance-user-endpoint \
    --app-instance-user-arn <value> \
    --endpoint-id <value> \
    [--name <value>] \
    [--allow-messages <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-user-arn` | **Yes** | string | -- | User ARN |
| `--endpoint-id` | **Yes** | string | -- | Endpoint ID |
| `--name` | No | string | None | Updated name |
| `--allow-messages` | No | string | None | `ALL` or `NONE` |

**Output Schema:**
```json
{
    "AppInstanceUserArn": "string",
    "EndpointId": "string"
}
```

---

### 2.11 `put-app-instance-user-expiration-settings`

Sets expiration settings for an AppInstanceUser.

**Synopsis:**
```bash
aws chime-sdk-identity put-app-instance-user-expiration-settings \
    --app-instance-user-arn <value> \
    [--expiration-settings <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-user-arn` | **Yes** | string | -- | User ARN |
| `--expiration-settings` | No | structure | None | Expiration settings (omit to remove) |

**ExpirationSettings structure:**
```json
{
    "ExpirationDays": 30,
    "ExpirationCriterion": "CREATED_TIMESTAMP"
}
```

**Output Schema:**
```json
{
    "AppInstanceUserArn": "string",
    "ExpirationSettings": {
        "ExpirationDays": "integer",
        "ExpirationCriterion": "CREATED_TIMESTAMP"
    }
}
```
