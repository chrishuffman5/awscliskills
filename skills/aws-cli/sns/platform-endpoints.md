# Platform Endpoints

### 6.1 `create-platform-endpoint`

Creates an endpoint for a device and mobile app on a push notification platform. Idempotent -- if an endpoint with the same token and attributes exists, returns its ARN.

**Synopsis:**
```bash
aws sns create-platform-endpoint \
    --platform-application-arn <value> \
    --token <value> \
    [--custom-user-data <value>] \
    [--attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--platform-application-arn` | **Yes** | string | -- | ARN of the platform application |
| `--token` | **Yes** | string | -- | Device token from the notification service (APNS device token, GCM/FCM registration ID) |
| `--custom-user-data` | No | string | None | Arbitrary user data. Max 2 KB. Not used by SNS |
| `--attributes` | No | map | None | Endpoint attributes (e.g., `Enabled`, `Token`) |

**Output Schema:**
```json
{
    "EndpointArn": "string"
}
```

---

### 6.2 `delete-endpoint`

Deletes the endpoint for a device and mobile app from Amazon SNS.

**Synopsis:**
```bash
aws sns delete-endpoint \
    --endpoint-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint to delete |

**Output Schema:** None

---

### 6.3 `get-endpoint-attributes`

Retrieves the endpoint attributes for a device on a push notification platform.

**Synopsis:**
```bash
aws sns get-endpoint-attributes \
    --endpoint-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint |

**Output Schema:**
```json
{
    "Attributes": {
        "CustomUserData": "string",
        "Enabled": "true|false",
        "Token": "string"
    }
}
```

---

### 6.4 `set-endpoint-attributes`

Sets the attributes for an endpoint on a push notification platform.

**Synopsis:**
```bash
aws sns set-endpoint-attributes \
    --endpoint-arn <value> \
    --attributes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the endpoint |
| `--attributes` | **Yes** | map | -- | Attributes to set: `CustomUserData`, `Enabled`, `Token` |

**Output Schema:** None

---

### 6.5 `list-endpoints-by-platform-application`

Lists the endpoints and attributes for devices in a supported push notification service. **Paginated operation** (max 100 per page). Rate limit: 30 TPS.

**Synopsis:**
```bash
aws sns list-endpoints-by-platform-application \
    --platform-application-arn <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--no-paginate] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--platform-application-arn` | **Yes** | string | -- | ARN of the platform application |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--max-items` | No | integer | None | Maximum total items to return |

**Output Schema:**
```json
{
    "Endpoints": [
        {
            "EndpointArn": "string",
            "Attributes": {
                "CustomUserData": "string",
                "Enabled": "true|false",
                "Token": "string"
            }
        }
    ],
    "NextToken": "string"
}
```
