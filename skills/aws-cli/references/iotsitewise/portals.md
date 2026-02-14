# Portals

### 5.1 `create-portal`

Creates a SiteWise Monitor portal for visualizing asset data.

**Synopsis:**
```bash
aws iotsitewise create-portal \
    --portal-name <value> \
    --portal-contact-email <value> \
    --role-arn <value> \
    [--portal-description <value>] \
    [--portal-logo-image-file <value>] \
    [--portal-auth-mode <value>] \
    [--portal-type <value>] \
    [--portal-type-configuration <value>] \
    [--notification-sender-email <value>] \
    [--alarms <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-name` | **Yes** | string | -- | Portal name (1-256 chars) |
| `--portal-contact-email` | **Yes** | string | -- | Admin contact email |
| `--role-arn` | **Yes** | string | -- | Service role ARN |
| `--portal-description` | No | string | None | Description (1-2048 chars) |
| `--portal-logo-image-file` | No | structure | None | Logo image (PNG, <1 MB) |
| `--portal-auth-mode` | No | string | `SSO` | `SSO` or `IAM` |
| `--portal-type` | No | string | None | `SITEWISE_PORTAL_V1` or `SITEWISE_PORTAL_V2` |
| `--portal-type-configuration` | No | map | None | Portal type config |
| `--notification-sender-email` | No | string | None | Alarm notification email (SES verified) |
| `--alarms` | No | structure | None | Alarm config with `alarmRoleArn` |
| `--tags` | No | map | None | Tags (max 50) |
| `--client-token` | No | string | Auto | Idempotency token |

**Alarms Structure:**
```json
{
    "alarmRoleArn": "string",
    "notificationLambdaArn": "string"
}
```

**Output Schema:**
```json
{
    "portalId": "string",
    "portalArn": "string",
    "portalStartUrl": "string",
    "portalStatus": {
        "state": "CREATING|PENDING|UPDATING|DELETING|ACTIVE|FAILED",
        "error": {
            "code": "INTERNAL_FAILURE|VALIDATION_ERROR|LIMIT_EXCEEDED",
            "message": "string"
        }
    },
    "ssoApplicationId": "string"
}
```

---

### 5.2 `describe-portal`

Describes a portal.

**Synopsis:**
```bash
aws iotsitewise describe-portal \
    --portal-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-id` | **Yes** | string | -- | Portal ID (UUID) |

**Output Schema:**
```json
{
    "portalId": "string",
    "portalArn": "string",
    "portalName": "string",
    "portalDescription": "string",
    "portalClientId": "string",
    "portalStartUrl": "string",
    "portalContactEmail": "string",
    "portalStatus": {
        "state": "CREATING|PENDING|UPDATING|DELETING|ACTIVE|FAILED",
        "error": {}
    },
    "portalCreationDate": "timestamp",
    "portalLastUpdateDate": "timestamp",
    "portalLogoImageLocation": {
        "id": "string",
        "url": "string"
    },
    "roleArn": "string",
    "portalAuthMode": "SSO|IAM",
    "notificationSenderEmail": "string",
    "alarms": {"alarmRoleArn": "string", "notificationLambdaArn": "string"},
    "portalType": "SITEWISE_PORTAL_V1|SITEWISE_PORTAL_V2",
    "portalTypeConfiguration": {}
}
```

---

### 5.3 `list-portals`

Lists portals. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-portals \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "portalSummaries": [
        {
            "id": "string",
            "name": "string",
            "description": "string",
            "startUrl": "string",
            "creationDate": "timestamp",
            "lastUpdateDate": "timestamp",
            "roleArn": "string",
            "status": {"state": "string", "error": {}}
        }
    ],
    "nextToken": "string"
}
```

---

### 5.4 `update-portal`

Updates a portal's name, description, contact email, logo, or role.

**Synopsis:**
```bash
aws iotsitewise update-portal \
    --portal-id <value> \
    --portal-name <value> \
    --portal-contact-email <value> \
    --role-arn <value> \
    [--portal-description <value>] \
    [--portal-logo-image <value>] \
    [--notification-sender-email <value>] \
    [--alarms <value>] \
    [--portal-type <value>] \
    [--portal-type-configuration <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-id` | **Yes** | string | -- | Portal ID |
| `--portal-name` | **Yes** | string | -- | Updated name |
| `--portal-contact-email` | **Yes** | string | -- | Updated contact email |
| `--role-arn` | **Yes** | string | -- | Updated role ARN |
| `--portal-description` | No | string | None | Updated description |
| `--portal-logo-image` | No | structure | None | Updated logo |
| `--notification-sender-email` | No | string | None | Updated notification email |
| `--alarms` | No | structure | None | Updated alarm config |
| `--portal-type` | No | string | None | Updated portal type |
| `--portal-type-configuration` | No | map | None | Updated type config |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "portalStatus": {
        "state": "UPDATING",
        "error": {}
    }
}
```

---

### 5.5 `delete-portal`

Deletes a portal. All projects and dashboards must be deleted first.

**Synopsis:**
```bash
aws iotsitewise delete-portal \
    --portal-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-id` | **Yes** | string | -- | Portal ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "portalStatus": {
        "state": "DELETING",
        "error": {}
    }
}
```
