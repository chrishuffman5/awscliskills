# Logging

### 5.1 `put-logging-configuration`

Enables logging for a web ACL. Logs can be sent to CloudWatch Logs, S3, or Kinesis Data Firehose.

**Synopsis:**
```bash
aws wafv2 put-logging-configuration \
    --logging-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--logging-configuration` | **Yes** | structure | -- | Logging configuration (JSON structure) |

**Logging Configuration Structure:**
```json
{
    "ResourceArn": "string",
    "LogDestinationConfigs": ["string"],
    "RedactedFields": [
        {
            "SingleHeader": {"Name": "string"},
            "SingleQueryArgument": {"Name": "string"},
            "AllQueryArguments": {},
            "UriPath": {},
            "QueryString": {},
            "Body": {"OversizeHandling": "CONTINUE|MATCH|NO_MATCH"},
            "Method": {},
            "JsonBody": {}
        }
    ],
    "ManagedByFirewallManager": "boolean",
    "LoggingFilter": {
        "Filters": [
            {
                "Behavior": "KEEP|DROP",
                "Requirement": "MEETS_ALL|MEETS_ANY",
                "Conditions": [
                    {
                        "ActionCondition": {
                            "Action": "ALLOW|BLOCK|COUNT|CAPTCHA|CHALLENGE|EXCLUDED_AS_COUNT"
                        },
                        "LabelNameCondition": {
                            "LabelName": "string"
                        }
                    }
                ]
            }
        ],
        "DefaultBehavior": "KEEP|DROP"
    },
    "LogType": "WAF_LOGS",
    "LogScope": "CUSTOMER|SECURITY_LAKE"
}
```

- `ResourceArn` — ARN of the web ACL to log.
- `LogDestinationConfigs` — Array with one destination ARN:
  - CloudWatch Logs: `arn:aws:logs:<region>:<account>:log-group:aws-waf-logs-<name>`
  - S3: `arn:aws:s3:::aws-waf-logs-<name>`
  - Kinesis Firehose: `arn:aws:firehose:<region>:<account>:deliverystream/aws-waf-logs-<name>`
- `RedactedFields` — Fields to redact from logs.
- `LoggingFilter` — Filter which requests are logged.

> **Note:** Log destination names must start with `aws-waf-logs-`.

**Output Schema:**
```json
{
    "LoggingConfiguration": {
        "ResourceArn": "string",
        "LogDestinationConfigs": ["string"],
        "RedactedFields": [],
        "ManagedByFirewallManager": "boolean",
        "LoggingFilter": {},
        "LogType": "string",
        "LogScope": "string"
    }
}
```

---

### 5.2 `get-logging-configuration`

Retrieves the logging configuration for a web ACL.

**Synopsis:**
```bash
aws wafv2 get-logging-configuration \
    --resource-arn <value> \
    [--log-type <value>] \
    [--log-scope <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the web ACL |
| `--log-type` | No | string | `WAF_LOGS` | Log type: `WAF_LOGS` |
| `--log-scope` | No | string | `CUSTOMER` | Log scope: `CUSTOMER` or `SECURITY_LAKE` |

**Output Schema:**
```json
{
    "LoggingConfiguration": {
        "ResourceArn": "string",
        "LogDestinationConfigs": ["string"],
        "RedactedFields": [],
        "ManagedByFirewallManager": "boolean",
        "LoggingFilter": {},
        "LogType": "string",
        "LogScope": "string"
    }
}
```

---

### 5.3 `delete-logging-configuration`

Deletes the logging configuration for a web ACL.

**Synopsis:**
```bash
aws wafv2 delete-logging-configuration \
    --resource-arn <value> \
    [--log-type <value>] \
    [--log-scope <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the web ACL |
| `--log-type` | No | string | `WAF_LOGS` | Log type |
| `--log-scope` | No | string | `CUSTOMER` | Log scope |

**Output:** None on success.

---

### 5.4 `list-logging-configurations`

Returns a list of logging configurations for all web ACLs in a scope. **Paginated operation.**

**Synopsis:**
```bash
aws wafv2 list-logging-configurations \
    --scope <value> \
    [--next-marker <value>] \
    [--limit <value>] \
    [--log-scope <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--next-marker` | No | string | None | Pagination token |
| `--limit` | No | integer | None | Maximum results |
| `--log-scope` | No | string | `CUSTOMER` | Log scope: `CUSTOMER` or `SECURITY_LAKE` |

**Output Schema:**
```json
{
    "LoggingConfigurations": [
        {
            "ResourceArn": "string",
            "LogDestinationConfigs": ["string"],
            "RedactedFields": [],
            "ManagedByFirewallManager": "boolean",
            "LoggingFilter": {},
            "LogType": "string",
            "LogScope": "string"
        }
    ],
    "NextMarker": "string"
}
```
