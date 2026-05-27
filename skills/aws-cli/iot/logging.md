# Logging

## 17.1 `get-logging-options`

Gets the legacy logging options.

**Synopsis:**
```bash
aws iot get-logging-options \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "roleArn": "string",
    "logLevel": "DEBUG|INFO|ERROR|WARN|DISABLED"
}
```

---

## 17.2 `set-logging-options`

Sets the legacy logging options.

**Synopsis:**
```bash
aws iot set-logging-options \
    --logging-options-payload <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--logging-options-payload` | **Yes** | structure | -- | `{roleArn: "string", logLevel: "DEBUG|INFO|ERROR|WARN|DISABLED"}` |

**Output:** None

---

## 17.3 `get-v2-logging-options`

Gets the v2 logging options.

**Synopsis:**
```bash
aws iot get-v2-logging-options \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "roleArn": "string",
    "defaultLogLevel": "DEBUG|INFO|ERROR|WARN|DISABLED",
    "disableAllLogs": "boolean"
}
```

---

## 17.4 `set-v2-logging-options`

Sets the v2 logging options.

**Synopsis:**
```bash
aws iot set-v2-logging-options \
    [--role-arn <value>] \
    [--default-log-level <value>] \
    [--disable-all-logs | --no-disable-all-logs] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-arn` | No | string | None | IAM role ARN for CloudWatch Logs |
| `--default-log-level` | No | string | None | `DEBUG`, `INFO`, `ERROR`, `WARN`, `DISABLED` |
| `--disable-all-logs` | No | boolean | false | Disable all logging |

**Output:** None

---

## 17.5 `list-v2-logging-levels`

Lists v2 logging levels per target. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-v2-logging-levels \
    [--target-type <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-type` | No | string | None | `DEFAULT`, `THING_GROUP`, `CLIENT_ID`, `SOURCE_IP`, `PRINCIPAL_ID` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "logTargetConfigurations": [
        {
            "logTarget": {
                "targetType": "DEFAULT|THING_GROUP|CLIENT_ID|SOURCE_IP|PRINCIPAL_ID",
                "targetName": "string"
            },
            "logLevel": "DEBUG|INFO|ERROR|WARN|DISABLED"
        }
    ],
    "nextToken": "string"
}
```

---

## 17.6 `set-v2-logging-level`

Sets a v2 logging level for a specific target.

**Synopsis:**
```bash
aws iot set-v2-logging-level \
    --log-target <value> \
    --log-level <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-target` | **Yes** | structure | -- | `{targetType: "THING_GROUP|CLIENT_ID|SOURCE_IP|PRINCIPAL_ID", targetName: "string"}` |
| `--log-level` | **Yes** | string | -- | `DEBUG`, `INFO`, `ERROR`, `WARN`, `DISABLED` |

**Output:** None

---

## 17.7 `delete-v2-logging-level`

Deletes a v2 logging level for a target.

**Synopsis:**
```bash
aws iot delete-v2-logging-level \
    --target-type <value> \
    --target-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-type` | **Yes** | string | -- | `DEFAULT`, `THING_GROUP`, `CLIENT_ID`, `SOURCE_IP`, `PRINCIPAL_ID` |
| `--target-name` | **Yes** | string | -- | Target name (e.g., thing group name) |

**Output:** None
