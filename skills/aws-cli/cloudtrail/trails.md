# Trails

### 1.1 `create-trail`

Creates a trail that specifies the settings for delivery of log data to an Amazon S3 bucket.

**Synopsis:**
```bash
aws cloudtrail create-trail \
    --name <value> \
    --s3-bucket-name <value> \
    [--s3-key-prefix <value>] \
    [--sns-topic-name <value>] \
    [--include-global-service-events | --no-include-global-service-events] \
    [--is-multi-region-trail | --no-is-multi-region-trail] \
    [--enable-log-file-validation | --no-enable-log-file-validation] \
    [--cloud-watch-logs-log-group-arn <value>] \
    [--cloud-watch-logs-role-arn <value>] \
    [--kms-key-id <value>] \
    [--is-organization-trail | --no-is-organization-trail] \
    [--tags-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trail name (3-128 chars, letters, numbers, periods, underscores, dashes) |
| `--s3-bucket-name` | **Yes** | string | -- | S3 bucket for log file delivery |
| `--s3-key-prefix` | No | string | None | S3 key prefix prepended to log file names |
| `--sns-topic-name` | No | string | None | SNS topic name for log file delivery notifications |
| `--include-global-service-events` | No | boolean | true | Include global service events (IAM, STS) |
| `--is-multi-region-trail` | No | boolean | false | Apply trail to all regions |
| `--enable-log-file-validation` | No | boolean | false | Enable log file integrity validation |
| `--cloud-watch-logs-log-group-arn` | No | string | None | CloudWatch Logs log group ARN for delivery |
| `--cloud-watch-logs-role-arn` | No | string | None | IAM role ARN for CloudWatch Logs delivery |
| `--kms-key-id` | No | string | None | KMS key ID or alias for SSE-KMS encryption |
| `--is-organization-trail` | No | boolean | false | Create an organization trail |
| `--tags-list` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Name": "string",
    "S3BucketName": "string",
    "S3KeyPrefix": "string",
    "SnsTopicName": "string",
    "SnsTopicARN": "string",
    "IncludeGlobalServiceEvents": true|false,
    "IsMultiRegionTrail": true|false,
    "TrailARN": "string",
    "LogFileValidationEnabled": true|false,
    "CloudWatchLogsLogGroupArn": "string",
    "CloudWatchLogsRoleArn": "string",
    "KmsKeyId": "string",
    "IsOrganizationTrail": true|false
}
```

---

### 1.2 `delete-trail`

Deletes a trail. Does not delete the S3 bucket or log files.

**Synopsis:**
```bash
aws cloudtrail delete-trail \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trail name or ARN |

**Output:** None (HTTP 200 on success)

---

### 1.3 `describe-trails`

Retrieves settings for one or more trails associated with the current region.

**Synopsis:**
```bash
aws cloudtrail describe-trails \
    [--trail-name-list <value>] \
    [--include-shadow-trails | --no-include-shadow-trails] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trail-name-list` | No | list(string) | None | Trail names or ARNs. Empty returns all trails |
| `--include-shadow-trails` | No | boolean | true | Include shadow trails (replicated multi-region trails) |

**Output Schema:**
```json
{
    "trailList": [
        {
            "Name": "string",
            "S3BucketName": "string",
            "S3KeyPrefix": "string",
            "SnsTopicName": "string",
            "SnsTopicARN": "string",
            "IncludeGlobalServiceEvents": true|false,
            "IsMultiRegionTrail": true|false,
            "HomeRegion": "string",
            "TrailARN": "string",
            "LogFileValidationEnabled": true|false,
            "CloudWatchLogsLogGroupArn": "string",
            "CloudWatchLogsRoleArn": "string",
            "KmsKeyId": "string",
            "HasCustomEventSelectors": true|false,
            "HasInsightSelectors": true|false,
            "IsOrganizationTrail": true|false
        }
    ]
}
```

---

### 1.4 `get-trail`

Returns settings for a trail, including the trail ARN, S3 bucket, and other configuration.

**Synopsis:**
```bash
aws cloudtrail get-trail \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trail name or ARN |

**Output Schema:**
```json
{
    "Trail": {
        "Name": "string",
        "S3BucketName": "string",
        "S3KeyPrefix": "string",
        "SnsTopicName": "string",
        "SnsTopicARN": "string",
        "IncludeGlobalServiceEvents": true|false,
        "IsMultiRegionTrail": true|false,
        "HomeRegion": "string",
        "TrailARN": "string",
        "LogFileValidationEnabled": true|false,
        "CloudWatchLogsLogGroupArn": "string",
        "CloudWatchLogsRoleArn": "string",
        "KmsKeyId": "string",
        "HasCustomEventSelectors": true|false,
        "HasInsightSelectors": true|false,
        "IsOrganizationTrail": true|false
    }
}
```

---

### 1.5 `list-trails`

Lists trails in the current account. **Paginated operation.**

**Synopsis:**
```bash
aws cloudtrail list-trails \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Trails": [
        {
            "TrailARN": "string",
            "Name": "string",
            "HomeRegion": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.6 `update-trail`

Updates the settings for a trail. Can change the S3 bucket, SNS topic, CloudWatch Logs, KMS encryption, and region scope.

**Synopsis:**
```bash
aws cloudtrail update-trail \
    --name <value> \
    [--s3-bucket-name <value>] \
    [--s3-key-prefix <value>] \
    [--sns-topic-name <value>] \
    [--include-global-service-events | --no-include-global-service-events] \
    [--is-multi-region-trail | --no-is-multi-region-trail] \
    [--enable-log-file-validation | --no-enable-log-file-validation] \
    [--cloud-watch-logs-log-group-arn <value>] \
    [--cloud-watch-logs-role-arn <value>] \
    [--kms-key-id <value>] \
    [--is-organization-trail | --no-is-organization-trail] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trail name or ARN |
| `--s3-bucket-name` | No | string | unchanged | S3 bucket for log file delivery |
| `--s3-key-prefix` | No | string | unchanged | S3 key prefix |
| `--sns-topic-name` | No | string | unchanged | SNS topic name for notifications |
| `--include-global-service-events` | No | boolean | unchanged | Include global service events |
| `--is-multi-region-trail` | No | boolean | unchanged | Apply trail to all regions |
| `--enable-log-file-validation` | No | boolean | unchanged | Enable log file integrity validation |
| `--cloud-watch-logs-log-group-arn` | No | string | unchanged | CloudWatch Logs log group ARN |
| `--cloud-watch-logs-role-arn` | No | string | unchanged | IAM role ARN for CloudWatch Logs |
| `--kms-key-id` | No | string | unchanged | KMS key ID or alias |
| `--is-organization-trail` | No | boolean | unchanged | Organization trail flag |

**Output Schema:**
```json
{
    "Name": "string",
    "S3BucketName": "string",
    "S3KeyPrefix": "string",
    "SnsTopicName": "string",
    "SnsTopicARN": "string",
    "IncludeGlobalServiceEvents": true|false,
    "IsMultiRegionTrail": true|false,
    "TrailARN": "string",
    "LogFileValidationEnabled": true|false,
    "CloudWatchLogsLogGroupArn": "string",
    "CloudWatchLogsRoleArn": "string",
    "KmsKeyId": "string",
    "IsOrganizationTrail": true|false
}
```

---

### 1.7 `start-logging`

Starts recording API calls and log file delivery for a trail.

**Synopsis:**
```bash
aws cloudtrail start-logging \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trail name or ARN |

**Output:** None (HTTP 200 on success)

---

### 1.8 `stop-logging`

Suspends recording of API calls and log file delivery for a trail. The trail remains but stops capturing events.

**Synopsis:**
```bash
aws cloudtrail stop-logging \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trail name or ARN |

**Output:** None (HTTP 200 on success)
