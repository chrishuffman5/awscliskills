# Security Controls

### 5.1 `list-security-control-definitions`

Lists all available security control definitions. **Paginated operation.**

**Synopsis:**
```bash
aws securityhub list-security-control-definitions \
    [--standards-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--standards-arn` | No | string | None | Filter by standard ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "SecurityControlDefinitions": [
        {
            "SecurityControlId": "string",
            "Title": "string",
            "Description": "string",
            "RemediationUrl": "string",
            "SeverityRating": "LOW|MEDIUM|HIGH|CRITICAL",
            "CurrentRegionAvailability": "AVAILABLE|UNAVAILABLE",
            "CustomizableProperties": ["Parameters"],
            "ParameterDefinitions": {
                "string": {
                    "Description": "string",
                    "ConfigurationOptions": {}
                }
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 5.2 `get-security-control-definition`

Returns the definition of a security control.

**Synopsis:**
```bash
aws securityhub get-security-control-definition \
    --security-control-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-control-id` | **Yes** | string | -- | Security control ID |

**Output Schema:**
```json
{
    "SecurityControlDefinition": {
        "SecurityControlId": "string",
        "Title": "string",
        "Description": "string",
        "RemediationUrl": "string",
        "SeverityRating": "LOW|MEDIUM|HIGH|CRITICAL",
        "CurrentRegionAvailability": "AVAILABLE|UNAVAILABLE",
        "CustomizableProperties": ["Parameters"],
        "ParameterDefinitions": {
            "string": {
                "Description": "string",
                "ConfigurationOptions": {}
            }
        }
    }
}
```

---

### 5.3 `batch-get-security-controls`

Returns details for a batch of security controls.

**Synopsis:**
```bash
aws securityhub batch-get-security-controls \
    --security-control-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-control-ids` | **Yes** | list(string) | -- | Security control IDs to retrieve |

**Output Schema:**
```json
{
    "SecurityControls": [
        {
            "SecurityControlId": "string",
            "SecurityControlArn": "string",
            "Title": "string",
            "Description": "string",
            "RemediationUrl": "string",
            "SeverityRating": "LOW|MEDIUM|HIGH|CRITICAL",
            "SecurityControlStatus": "ENABLED|DISABLED",
            "UpdateStatus": "READY|UPDATING",
            "Parameters": {
                "string": {
                    "ValueType": "DEFAULT|CUSTOM",
                    "Value": {}
                }
            },
            "LastUpdateReason": "string"
        }
    ],
    "UnprocessedIds": [
        {
            "SecurityControlId": "string",
            "ErrorCode": "string",
            "ErrorReason": "string"
        }
    ]
}
```

---

### 5.4 `update-security-control`

Updates the properties of a security control.

**Synopsis:**
```bash
aws securityhub update-security-control \
    --security-control-id <value> \
    --parameters <value> \
    [--last-update-reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-control-id` | **Yes** | string | -- | Security control ID |
| `--parameters` | **Yes** | map | -- | Control parameters to update |
| `--last-update-reason` | No | string | None | Reason for the update |

**Parameters Structure:**
```json
{
    "string": {
        "ValueType": "DEFAULT|CUSTOM",
        "Value": {
            "Integer": "integer",
            "IntegerList": ["integer"],
            "Double": "double",
            "String": "string",
            "StringList": ["string"],
            "Boolean": "boolean",
            "Enum": "string",
            "EnumList": ["string"]
        }
    }
}
```

**Output:** None (HTTP 200 on success)
