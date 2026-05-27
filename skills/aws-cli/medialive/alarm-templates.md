# CloudWatch Alarm Templates

### 12.1 `create-cloud-watch-alarm-template`

Creates a CloudWatch alarm template for automated monitoring of MediaLive resources.

**Synopsis:**
```bash
aws medialive create-cloud-watch-alarm-template \
    --comparison-operator <value> \
    --evaluation-periods <value> \
    --group-identifier <value> \
    --metric-name <value> \
    --name <value> \
    --period <value> \
    --statistic <value> \
    --target-resource-type <value> \
    --threshold <value> \
    --treat-missing-data <value> \
    [--datapoints-to-alarm <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--comparison-operator` | **Yes** | string | -- | `GreaterThanOrEqualToThreshold`, `GreaterThanThreshold`, `LessThanThreshold`, `LessThanOrEqualToThreshold` |
| `--evaluation-periods` | **Yes** | integer | -- | Periods to evaluate |
| `--group-identifier` | **Yes** | string | -- | Alarm template group ID or name |
| `--metric-name` | **Yes** | string | -- | CloudWatch metric name |
| `--name` | **Yes** | string | -- | Template name (unique per region) |
| `--period` | **Yes** | integer | -- | Period in seconds |
| `--statistic` | **Yes** | string | -- | `SampleCount`, `Average`, `Sum`, `Minimum`, `Maximum` |
| `--target-resource-type` | **Yes** | string | -- | `CLOUDFRONT_DISTRIBUTION`, `MEDIALIVE_MULTIPLEX`, `MEDIALIVE_CHANNEL`, `MEDIALIVE_INPUT_DEVICE`, `MEDIAPACKAGE_CHANNEL`, `MEDIAPACKAGE_ORIGIN_ENDPOINT`, `MEDIACONNECT_FLOW`, `S3_BUCKET` |
| `--threshold` | **Yes** | double | -- | Threshold value |
| `--treat-missing-data` | **Yes** | string | -- | `notBreaching`, `breaching`, `ignore`, `missing` |
| `--datapoints-to-alarm` | No | integer | None | Datapoints to trigger alarm |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Key-value tag pairs |
| `--request-id` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "GroupId": "string",
    "ComparisonOperator": "string",
    "EvaluationPeriods": "integer",
    "MetricName": "string",
    "Period": "integer",
    "Statistic": "string",
    "TargetResourceType": "string",
    "Threshold": "double",
    "TreatMissingData": "string",
    "DatapointsToAlarm": "integer",
    "Description": "string",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "Tags": {}
}
```

---

### 12.2 `get-cloud-watch-alarm-template`

Gets a CloudWatch alarm template.

**Synopsis:**
```bash
aws medialive get-cloud-watch-alarm-template \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Template ID |

**Output Schema:** Same as `create-cloud-watch-alarm-template` output.

---

### 12.3 `update-cloud-watch-alarm-template`

Updates a CloudWatch alarm template.

**Synopsis:**
```bash
aws medialive update-cloud-watch-alarm-template \
    --identifier <value> \
    [--comparison-operator <value>] \
    [--datapoints-to-alarm <value>] \
    [--description <value>] \
    [--evaluation-periods <value>] \
    [--group-identifier <value>] \
    [--metric-name <value>] \
    [--name <value>] \
    [--period <value>] \
    [--statistic <value>] \
    [--target-resource-type <value>] \
    [--threshold <value>] \
    [--treat-missing-data <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Template ID to update |
| All other params | No | various | None | Same as create, all optional for update |

**Output Schema:** Same as `create-cloud-watch-alarm-template` output.

---

### 12.4 `delete-cloud-watch-alarm-template`

Deletes a CloudWatch alarm template.

**Synopsis:**
```bash
aws medialive delete-cloud-watch-alarm-template \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Template ID to delete |

**Output:** None

---

### 12.5 `list-cloud-watch-alarm-templates`

Lists CloudWatch alarm templates. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-cloud-watch-alarm-templates \
    [--group-identifier <value>] \
    [--scope <value>] \
    [--signal-map-identifier <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-identifier` | No | string | None | Filter by group |
| `--scope` | No | string | None | Filter scope |
| `--signal-map-identifier` | No | string | None | Filter by signal map |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "CloudWatchAlarmTemplates": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "GroupId": "string",
            "ComparisonOperator": "string",
            "MetricName": "string",
            "TargetResourceType": "string",
            "CreatedAt": "timestamp",
            "ModifiedAt": "timestamp",
            "Tags": {}
        }
    ]
}
```

---

### 12.6 `create-cloud-watch-alarm-template-group`

Creates a group for organizing CloudWatch alarm templates.

**Synopsis:**
```bash
aws medialive create-cloud-watch-alarm-template-group \
    --name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Group name (unique per region) |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Key-value tag pairs |
| `--request-id` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "TemplateCount": "integer",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "Tags": {}
}
```

---

### 12.7 `get-cloud-watch-alarm-template-group`

Gets a CloudWatch alarm template group.

**Synopsis:**
```bash
aws medialive get-cloud-watch-alarm-template-group \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Group ID |

**Output Schema:** Same as `create-cloud-watch-alarm-template-group` output.

---

### 12.8 `update-cloud-watch-alarm-template-group`

Updates a CloudWatch alarm template group.

**Synopsis:**
```bash
aws medialive update-cloud-watch-alarm-template-group \
    --identifier <value> \
    [--description <value>] \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Group ID |
| `--description` | No | string | None | Updated description |
| `--name` | No | string | None | Updated name |

**Output Schema:** Same as `create-cloud-watch-alarm-template-group` output.

---

### 12.9 `delete-cloud-watch-alarm-template-group`

Deletes a CloudWatch alarm template group.

**Synopsis:**
```bash
aws medialive delete-cloud-watch-alarm-template-group \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Group ID to delete |

**Output:** None

---

### 12.10 `list-cloud-watch-alarm-template-groups`

Lists CloudWatch alarm template groups. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-cloud-watch-alarm-template-groups \
    [--signal-map-identifier <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--signal-map-identifier` | No | string | None | Filter by signal map |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "CloudWatchAlarmTemplateGroups": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "TemplateCount": "integer",
            "CreatedAt": "timestamp",
            "ModifiedAt": "timestamp",
            "Tags": {}
        }
    ]
}
```
