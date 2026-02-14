# Suite Definitions

### 1.1 `create-suite-definition`

Creates a test suite definition with test configuration, target devices, and MQTT protocol settings.

**Synopsis:**
```bash
aws iotdeviceadvisor create-suite-definition \
    --suite-definition-configuration <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--suite-definition-configuration` | **Yes** | structure | -- | Suite definition configuration |
| `--tags` | No | map | None | Key-value tag pairs (max 50) |
| `--client-token` | No | string | Auto | Idempotency token (1-64 chars) |

**SuiteDefinitionConfiguration:**
```json
{
    "suiteDefinitionName": "string",
    "rootGroup": "string",
    "devicePermissionRoleArn": "string",
    "devices": [
        {
            "thingArn": "string",
            "certificateArn": "string",
            "deviceRoleArn": "string"
        }
    ],
    "intendedForQualification": true,
    "isLongDurationTest": false,
    "protocol": "MqttV3_1_1|MqttV5|MqttV3_1_1_OverWebSocket|MqttV5_OverWebSocket"
}
```

- `suiteDefinitionName` (required) — Name (1-256 chars)
- `rootGroup` (required) — JSON string defining test cases and groups (0-2048 chars; can be empty only if `intendedForQualification` is true)
- `devicePermissionRoleArn` (required) — IAM role ARN for device permissions (20-2048 chars)
- `devices` (optional) — Up to 2 test devices
- `intendedForQualification` (optional) — Whether for AWS IoT qualification
- `isLongDurationTest` (optional) — Long duration test flag
- `protocol` (optional) — MQTT protocol version

**Output Schema:**
```json
{
    "suiteDefinitionId": "string",
    "suiteDefinitionArn": "string",
    "suiteDefinitionName": "string",
    "createdAt": "timestamp"
}
```

---

### 1.2 `get-suite-definition`

Gets the details of a test suite definition.

**Synopsis:**
```bash
aws iotdeviceadvisor get-suite-definition \
    --suite-definition-id <value> \
    [--suite-definition-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--suite-definition-id` | **Yes** | string | -- | Suite definition ID (12-36 chars) |
| `--suite-definition-version` | No | string | None | Specific version (2-255 chars) |

**Output Schema:**
```json
{
    "suiteDefinitionId": "string",
    "suiteDefinitionArn": "string",
    "suiteDefinitionVersion": "string",
    "latestVersion": "string",
    "suiteDefinitionConfiguration": {
        "suiteDefinitionName": "string",
        "devices": [],
        "intendedForQualification": "boolean",
        "isLongDurationTest": "boolean",
        "rootGroup": "string",
        "devicePermissionRoleArn": "string",
        "protocol": "string"
    },
    "createdAt": "timestamp",
    "lastModifiedAt": "timestamp",
    "tags": {}
}
```

---

### 1.3 `update-suite-definition`

Updates a test suite definition's configuration.

**Synopsis:**
```bash
aws iotdeviceadvisor update-suite-definition \
    --suite-definition-id <value> \
    --suite-definition-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--suite-definition-id` | **Yes** | string | -- | Suite definition ID to update (12-36 chars) |
| `--suite-definition-configuration` | **Yes** | structure | -- | Updated configuration (same structure as create) |

**Output Schema:**
```json
{
    "suiteDefinitionId": "string",
    "suiteDefinitionArn": "string",
    "suiteDefinitionName": "string",
    "suiteDefinitionVersion": "string",
    "createdAt": "timestamp",
    "lastUpdatedAt": "timestamp"
}
```

---

### 1.4 `delete-suite-definition`

Deletes a test suite definition.

**Synopsis:**
```bash
aws iotdeviceadvisor delete-suite-definition \
    --suite-definition-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--suite-definition-id` | **Yes** | string | -- | Suite definition ID to delete (12-36 chars) |

**Output:** None

---

### 1.5 `list-suite-definitions`

Lists all test suite definitions. **Paginated operation.**

**Synopsis:**
```bash
aws iotdeviceadvisor list-suite-definitions \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "nextToken": "string",
    "suiteDefinitionInformationList": [
        {
            "suiteDefinitionId": "string",
            "suiteDefinitionName": "string",
            "defaultDevices": [
                {
                    "thingArn": "string",
                    "certificateArn": "string",
                    "deviceRoleArn": "string"
                }
            ],
            "intendedForQualification": "boolean",
            "isLongDurationTest": "boolean",
            "protocol": "string",
            "createdAt": "timestamp"
        }
    ]
}
```

---

### 1.6 `get-endpoint`

Gets the Device Advisor test endpoint for device testing. Returns an account-level or device-level endpoint.

**Synopsis:**
```bash
aws iotdeviceadvisor get-endpoint \
    [--thing-arn <value>] \
    [--certificate-arn <value>] \
    [--device-role-arn <value>] \
    [--authentication-method <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-arn` | No | string | None | Device thing ARN (20-2048 chars) |
| `--certificate-arn` | No | string | None | Device certificate ARN (20-2048 chars) |
| `--device-role-arn` | No | string | None | Device role ARN (20-2048 chars) |
| `--authentication-method` | No | string | None | `X509ClientCertificate` or `SignatureVersion4` |

When called with no parameters, returns an account-level endpoint. When called with device-specific ARNs, returns a device-level endpoint.

**Output Schema:**
```json
{
    "endpoint": "string"
}
```
