# Detect

Device Defender Detect monitors device behavior against security profiles.

## 10.1 `create-security-profile`

Creates a Device Defender security profile with behavior rules.

**Synopsis:**
```bash
aws iot create-security-profile \
    --security-profile-name <value> \
    [--security-profile-description <value>] \
    [--behaviors <value>] \
    [--alert-targets <value>] \
    [--additional-metrics-to-retain-v2 <value>] \
    [--tags <value>] \
    [--metrics-export-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-name` | **Yes** | string | -- | Profile name (1-128 chars) |
| `--security-profile-description` | No | string | None | Description (max 1000 chars) |
| `--behaviors` | No | list | None | Behavior rules (max 100). Each: name, metric, criteria |
| `--alert-targets` | No | map | None | SNS alert targets |
| `--additional-metrics-to-retain-v2` | No | list | None | Additional metrics to retain |
| `--tags` | No | list | None | Tags |
| `--metrics-export-config` | No | structure | None | MQTT topic and role for metric export |

**Behavior structure:**
```json
{
    "name": "string",
    "metric": "string",
    "metricDimension": {"dimensionName": "string", "operator": "IN|NOT_IN"},
    "criteria": {
        "comparisonOperator": "less-than|less-than-equals|greater-than|greater-than-equals|in-cidr-set|not-in-cidr-set|in-port-set|not-in-port-set|in-set|not-in-set",
        "value": {"count": "long", "cidrs": [], "ports": [], "number": "double", "numbers": [], "strings": []},
        "durationSeconds": "integer",
        "consecutiveDatapointsToAlarm": "integer",
        "consecutiveDatapointsToClear": "integer",
        "statisticalThreshold": {"statistic": "string"},
        "mlDetectionConfig": {"confidenceLevel": "LOW|MEDIUM|HIGH"}
    },
    "suppressAlerts": "boolean",
    "exportMetric": "boolean"
}
```

**Output Schema:**
```json
{
    "securityProfileName": "string",
    "securityProfileArn": "string"
}
```

---

## 10.2 `describe-security-profile`

Describes a security profile.

**Synopsis:**
```bash
aws iot describe-security-profile \
    --security-profile-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-name` | **Yes** | string | -- | Profile name |

**Output Schema:**
```json
{
    "securityProfileName": "string",
    "securityProfileArn": "string",
    "securityProfileDescription": "string",
    "behaviors": [],
    "alertTargets": {},
    "additionalMetricsToRetainV2": [],
    "version": "long",
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp",
    "metricsExportConfig": {}
}
```

---

## 10.3 `list-security-profiles`

Lists security profiles. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-security-profiles \
    [--next-token <value>] \
    [--max-results <value>] \
    [--dimension-name <value>] \
    [--metric-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |
| `--dimension-name` | No | string | None | Filter by dimension |
| `--metric-name` | No | string | None | Filter by metric |

**Output Schema:**
```json
{
    "securityProfileIdentifiers": [
        {"name": "string", "arn": "string"}
    ],
    "nextToken": "string"
}
```

---

## 10.4 `update-security-profile`

Updates a security profile.

**Synopsis:**
```bash
aws iot update-security-profile \
    --security-profile-name <value> \
    [--security-profile-description <value>] \
    [--behaviors <value>] \
    [--alert-targets <value>] \
    [--additional-metrics-to-retain-v2 <value>] \
    [--delete-behaviors | --no-delete-behaviors] \
    [--delete-alert-targets | --no-delete-alert-targets] \
    [--delete-additional-metrics-to-retain | --no-delete-additional-metrics-to-retain] \
    [--expected-version <value>] \
    [--metrics-export-config <value>] \
    [--delete-metrics-export-config | --no-delete-metrics-export-config] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-name` | **Yes** | string | -- | Profile name |
| `--security-profile-description` | No | string | None | Updated description |
| `--behaviors` | No | list | None | Updated behaviors |
| `--alert-targets` | No | map | None | Updated alert targets |
| `--additional-metrics-to-retain-v2` | No | list | None | Updated metrics |
| `--delete-behaviors` | No | boolean | false | Delete all behaviors |
| `--delete-alert-targets` | No | boolean | false | Delete all alert targets |
| `--delete-additional-metrics-to-retain` | No | boolean | false | Delete retained metrics |
| `--expected-version` | No | long | None | Expected version |
| `--metrics-export-config` | No | structure | None | Updated metrics export |
| `--delete-metrics-export-config` | No | boolean | false | Delete export config |

**Output Schema:**
```json
{
    "securityProfileName": "string",
    "securityProfileArn": "string",
    "securityProfileDescription": "string",
    "behaviors": [],
    "alertTargets": {},
    "additionalMetricsToRetainV2": [],
    "version": "long",
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp",
    "metricsExportConfig": {}
}
```

---

## 10.5 `delete-security-profile`

Deletes a security profile.

**Synopsis:**
```bash
aws iot delete-security-profile \
    --security-profile-name <value> \
    [--expected-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-name` | **Yes** | string | -- | Profile name |
| `--expected-version` | No | long | None | Expected version |

**Output:** None

---

## 10.6 `attach-security-profile`

Attaches a security profile to a target (thing group or all things).

**Synopsis:**
```bash
aws iot attach-security-profile \
    --security-profile-name <value> \
    --security-profile-target-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-name` | **Yes** | string | -- | Profile name |
| `--security-profile-target-arn` | **Yes** | string | -- | Target ARN (thing group or `arn:aws:iot:<region>:<account>:all/things`) |

**Output:** None

---

## 10.7 `detach-security-profile`

Detaches a security profile from a target.

**Synopsis:**
```bash
aws iot detach-security-profile \
    --security-profile-name <value> \
    --security-profile-target-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-name` | **Yes** | string | -- | Profile name |
| `--security-profile-target-arn` | **Yes** | string | -- | Target ARN |

**Output:** None

---

## 10.8 `list-security-profiles-for-target`

Lists security profiles for a target. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-security-profiles-for-target \
    --security-profile-target-arn <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--recursive | --no-recursive] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-target-arn` | **Yes** | string | -- | Target ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |
| `--recursive` | No | boolean | false | Include inherited profiles |

**Output Schema:**
```json
{
    "securityProfileTargetMappings": [
        {
            "securityProfileIdentifier": {"name": "string", "arn": "string"},
            "target": {"arn": "string"}
        }
    ],
    "nextToken": "string"
}
```

---

## 10.9 `list-targets-for-security-profile`

Lists targets for a security profile. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-targets-for-security-profile \
    --security-profile-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-name` | **Yes** | string | -- | Profile name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "securityProfileTargets": [
        {"arn": "string"}
    ],
    "nextToken": "string"
}
```

---

## 10.10 `create-custom-metric`

Creates a Device Defender custom metric.

**Synopsis:**
```bash
aws iot create-custom-metric \
    --metric-name <value> \
    --metric-type <value> \
    --client-request-token <value> \
    [--display-name <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-name` | **Yes** | string | -- | Metric name (1-128 chars) |
| `--metric-type` | **Yes** | string | -- | `string-list`, `ip-address-list`, `number-list`, `number` |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |
| `--display-name` | No | string | None | Display name |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "metricName": "string",
    "metricArn": "string"
}
```

---

## 10.11 `describe-custom-metric`

Describes a custom metric.

**Synopsis:**
```bash
aws iot describe-custom-metric \
    --metric-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-name` | **Yes** | string | -- | Metric name |

**Output Schema:**
```json
{
    "metricName": "string",
    "metricArn": "string",
    "metricType": "string-list|ip-address-list|number-list|number",
    "displayName": "string",
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp"
}
```

---

## 10.12 `list-custom-metrics`

Lists custom metrics. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-custom-metrics \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "metricNames": ["string"],
    "nextToken": "string"
}
```

---

## 10.13 `update-custom-metric`

Updates a custom metric display name.

**Synopsis:**
```bash
aws iot update-custom-metric \
    --metric-name <value> \
    --display-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-name` | **Yes** | string | -- | Metric name |
| `--display-name` | **Yes** | string | -- | Updated display name |

**Output Schema:**
```json
{
    "metricName": "string",
    "metricArn": "string",
    "metricType": "string",
    "displayName": "string",
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp"
}
```

---

## 10.14 `delete-custom-metric`

Deletes a custom metric.

**Synopsis:**
```bash
aws iot delete-custom-metric \
    --metric-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-name` | **Yes** | string | -- | Metric name |

**Output:** None

---

## 10.15 `create-dimension`

Creates a dimension for scoping security profile behaviors.

**Synopsis:**
```bash
aws iot create-dimension \
    --name <value> \
    --type <value> \
    --string-values <value> \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Dimension name (1-128 chars) |
| `--type` | **Yes** | string | -- | `TOPIC_FILTER` |
| `--string-values` | **Yes** | list | -- | MQTT topic patterns (1-100 values) |
| `--tags` | No | list | None | Tags |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```

---

## 10.16 `describe-dimension`

Describes a dimension.

**Synopsis:**
```bash
aws iot describe-dimension \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Dimension name |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string",
    "type": "TOPIC_FILTER",
    "stringValues": ["string"],
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp"
}
```

---

## 10.17 `list-dimensions`

Lists dimensions. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-dimensions \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "dimensionNames": ["string"],
    "nextToken": "string"
}
```

---

## 10.18 `update-dimension`

Updates a dimension's values.

**Synopsis:**
```bash
aws iot update-dimension \
    --name <value> \
    --string-values <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Dimension name |
| `--string-values` | **Yes** | list | -- | Updated topic patterns |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string",
    "type": "TOPIC_FILTER",
    "stringValues": ["string"],
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp"
}
```

---

## 10.19 `delete-dimension`

Deletes a dimension.

**Synopsis:**
```bash
aws iot delete-dimension \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Dimension name |

**Output:** None

---

## 10.20 `list-active-violations`

Lists active Device Defender violations. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-active-violations \
    [--thing-name <value>] \
    [--security-profile-name <value>] \
    [--behavior-criteria-type <value>] \
    [--list-suppressed-alerts | --no-list-suppressed-alerts] \
    [--verification-state <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | No | string | None | Filter by thing |
| `--security-profile-name` | No | string | None | Filter by profile |
| `--behavior-criteria-type` | No | string | None | `STATIC`, `STATISTICAL`, `MACHINE_LEARNING` |
| `--list-suppressed-alerts` | No | boolean | false | Include suppressed |
| `--verification-state` | No | string | None | `FALSE_POSITIVE`, `BENIGN_POSITIVE`, `TRUE_POSITIVE`, `UNKNOWN` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "activeViolations": [
        {
            "violationId": "string",
            "thingName": "string",
            "securityProfileName": "string",
            "behavior": {},
            "lastViolationValue": {},
            "violationEventAdditionalInfo": {},
            "verificationState": "string",
            "verificationStateDescription": "string",
            "lastViolationTime": "timestamp",
            "violationStartTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 10.21 `list-violation-events`

Lists Device Defender violation events. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-violation-events \
    --start-time <value> \
    --end-time <value> \
    [--thing-name <value>] \
    [--security-profile-name <value>] \
    [--behavior-criteria-type <value>] \
    [--list-suppressed-alerts | --no-list-suppressed-alerts] \
    [--verification-state <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-time` | **Yes** | timestamp | -- | Start of time range |
| `--end-time` | **Yes** | timestamp | -- | End of time range |
| `--thing-name` | No | string | None | Filter by thing |
| `--security-profile-name` | No | string | None | Filter by profile |
| `--behavior-criteria-type` | No | string | None | Filter by criteria type |
| `--list-suppressed-alerts` | No | boolean | false | Include suppressed |
| `--verification-state` | No | string | None | Filter by verification state |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "violationEvents": [
        {
            "violationId": "string",
            "thingName": "string",
            "securityProfileName": "string",
            "behavior": {},
            "metricValue": {},
            "violationEventAdditionalInfo": {},
            "violationEventType": "in-alarm|alarm-cleared|alarm-invalidated",
            "verificationState": "string",
            "verificationStateDescription": "string",
            "violationEventTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 10.22 `put-verification-state-on-violation`

Sets the verification state on a violation.

**Synopsis:**
```bash
aws iot put-verification-state-on-violation \
    --violation-id <value> \
    --verification-state <value> \
    [--verification-state-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--violation-id` | **Yes** | string | -- | Violation ID |
| `--verification-state` | **Yes** | string | -- | `FALSE_POSITIVE`, `BENIGN_POSITIVE`, `TRUE_POSITIVE`, `UNKNOWN` |
| `--verification-state-description` | No | string | None | Description |

**Output:** None

---

## 10.23 `get-behavior-model-training-summaries`

Gets ML Detect behavior model training summaries.

**Synopsis:**
```bash
aws iot get-behavior-model-training-summaries \
    [--security-profile-name <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-name` | No | string | None | Filter by profile |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "summaries": [
        {
            "securityProfileName": "string",
            "behaviorName": "string",
            "trainingDataCollectionStartDate": "timestamp",
            "modelStatus": "PENDING_BUILD|ACTIVE|EXPIRED",
            "datapointsCollectionPercentage": "double",
            "lastModelRefreshDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 10.24-10.28 Detect Mitigation Actions

`start-detect-mitigation-actions-task`, `describe-detect-mitigation-actions-task`, `list-detect-mitigation-actions-tasks`, `list-detect-mitigation-actions-executions`, and `cancel-detect-mitigation-actions-task` follow the same pattern as audit mitigation actions (see [audit.md](audit.md) sections 9.25-9.29) but operate on Detect violations instead of audit findings.

---

## 10.29 `list-metric-values`

Lists metric values for Device Defender. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-metric-values \
    --thing-name <value> \
    --metric-name <value> \
    --start-time <value> \
    --end-time <value> \
    [--dimension-name <value>] \
    [--dimension-value-operator <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--metric-name` | **Yes** | string | -- | Metric name |
| `--start-time` | **Yes** | timestamp | -- | Start time |
| `--end-time` | **Yes** | timestamp | -- | End time |
| `--dimension-name` | No | string | None | Dimension name |
| `--dimension-value-operator` | No | string | None | `IN` or `NOT_IN` |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "metricDatumList": [
        {
            "timestamp": "timestamp",
            "value": {
                "count": "long",
                "cidrs": ["string"],
                "ports": ["integer"],
                "number": "double",
                "numbers": ["double"],
                "strings": ["string"]
            }
        }
    ],
    "nextToken": "string"
}
```

---

## 10.30 `validate-security-profile-behaviors`

Validates security profile behaviors without creating a profile.

**Synopsis:**
```bash
aws iot validate-security-profile-behaviors \
    --behaviors <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--behaviors` | **Yes** | list | -- | Behaviors to validate |

**Output Schema:**
```json
{
    "valid": "boolean",
    "validationErrors": [
        {"errorMessage": "string"}
    ]
}
```
