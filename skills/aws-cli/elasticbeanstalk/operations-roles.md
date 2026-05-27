# Operations & Roles

### 7.1 `describe-events`

Returns list of event descriptions matching criteria. **Paginated operation.**

**Synopsis:**
```bash
aws elasticbeanstalk describe-events \
    [--application-name <value>] \
    [--version-label <value>] \
    [--template-name <value>] \
    [--environment-id <value>] \
    [--environment-name <value>] \
    [--platform-arn <value>] \
    [--request-id <value>] \
    [--severity <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | No | string | -- | Filter by application name |
| `--version-label` | No | string | -- | Filter by version label |
| `--template-name` | No | string | -- | Filter by template name |
| `--environment-id` | No | string | -- | Filter by environment ID |
| `--environment-name` | No | string | -- | Filter by environment name |
| `--platform-arn` | No | string | -- | Filter by platform ARN |
| `--request-id` | No | string | -- | Filter by request ID |
| `--severity` | No | string | -- | Min severity: `TRACE`, `DEBUG`, `INFO`, `WARN`, `ERROR`, `FATAL` |
| `--start-time` | No | timestamp | -- | Start of time range |
| `--end-time` | No | timestamp | -- | End of time range |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Events": [
        {
            "EventDate": "timestamp",
            "Message": "string",
            "ApplicationName": "string",
            "VersionLabel": "string",
            "TemplateName": "string",
            "EnvironmentName": "string",
            "PlatformArn": "string",
            "RequestId": "string",
            "Severity": "TRACE|DEBUG|INFO|WARN|ERROR|FATAL"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.2 `describe-account-attributes`

Returns attributes related to the Elastic Beanstalk account limits and current usage.

**Synopsis:**
```bash
aws elasticbeanstalk describe-account-attributes \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

This command takes no service-specific parameters.

**Output Schema:**
```json
{
    "ResourceQuotas": {
        "ApplicationQuota": {"Maximum": "integer"},
        "ApplicationVersionQuota": {"Maximum": "integer"},
        "EnvironmentQuota": {"Maximum": "integer"},
        "ConfigurationTemplateQuota": {"Maximum": "integer"},
        "CustomPlatformQuota": {"Maximum": "integer"}
    }
}
```

---

### 7.3 `create-storage-location`

Creates an Amazon S3 bucket for storing Elastic Beanstalk storage artifacts in the specified region.

**Synopsis:**
```bash
aws elasticbeanstalk create-storage-location \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

This command takes no service-specific parameters.

**Output Schema:**
```json
{
    "S3Bucket": "string"
}
```

---

### 7.4 `associate-environment-operations-role`

Adds the specified operations role to the specified environment. After this call, Elastic Beanstalk uses the specified role for all future operations.

**Synopsis:**
```bash
aws elasticbeanstalk associate-environment-operations-role \
    --environment-name <value> \
    --operations-role <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-name` | **Yes** | string | -- | Environment name |
| `--operations-role` | **Yes** | string | -- | IAM role ARN for environment operations |

**Output Schema:**
```json
{}
```

---

### 7.5 `disassociate-environment-operations-role`

Disassociates the operations role from the specified environment.

**Synopsis:**
```bash
aws elasticbeanstalk disassociate-environment-operations-role \
    --environment-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-name` | **Yes** | string | -- | Environment name |

**Output Schema:**
```json
{}
```
