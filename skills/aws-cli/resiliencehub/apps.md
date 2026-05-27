# Apps

### 1.1 `create-app`

Creates a Resilience Hub application.

**Synopsis:**
```bash
aws resiliencehub create-app \
    --name <value> \
    [--description <value>] \
    [--assessment-schedule <value>] \
    [--policy-arn <value>] \
    [--event-subscriptions <value>] \
    [--permission-model <value>] \
    [--aws-application-arn <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Application name (pattern: `^[A-Za-z0-9][A-Za-z0-9_\-]{1,59}$`) |
| `--description` | No | string | None | Description (0-500 chars) |
| `--assessment-schedule` | No | string | None | `Disabled` or `Daily` |
| `--policy-arn` | No | string | None | Resiliency policy ARN |
| `--event-subscriptions` | No | list | None | Event subscriptions (max 10). JSON: `[{eventType,name,snsTopicArn}]` |
| `--permission-model` | No | structure | None | Permission model. Shorthand: `type=LegacyIAMUser\|RoleBased,invokerRoleName=string` |
| `--aws-application-arn` | No | string | None | AppRegistry application ARN |
| `--client-token` | No | string | Auto | Idempotency token (1-63 chars) |
| `--tags` | No | map | None | Tags (1-50 tags) |

**Output Schema:**
```json
{
    "app": {
        "appArn": "string",
        "name": "string",
        "description": "string",
        "status": "Active|Deleting",
        "complianceStatus": "PolicyBreached|PolicyMet|NotAssessed|ChangesDetected|NotApplicable|MissingPolicy",
        "driftStatus": "NotChecked|NotDetected|Detected",
        "resiliencyScore": "double",
        "rtoInSecs": "integer",
        "rpoInSecs": "integer",
        "assessmentSchedule": "Disabled|Daily",
        "policyArn": "string",
        "creationTime": "timestamp",
        "tags": {"string": "string"},
        "permissionModel": {},
        "eventSubscriptions": []
    }
}
```

---

### 1.2 `delete-app`

Deletes a Resilience Hub application.

**Synopsis:**
```bash
aws resiliencehub delete-app \
    --app-arn <value> \
    [--force-delete | --no-force-delete] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--force-delete` | No | boolean | false | Force delete even with assessments |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "appArn": "string"
}
```

---

### 1.3 `describe-app`

Describes a Resilience Hub application.

**Synopsis:**
```bash
aws resiliencehub describe-app \
    --app-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |

**Output Schema:**
```json
{
    "app": {
        "appArn": "string",
        "name": "string",
        "description": "string",
        "status": "Active|Deleting",
        "complianceStatus": "string",
        "driftStatus": "string",
        "resiliencyScore": "double",
        "rtoInSecs": "integer",
        "rpoInSecs": "integer",
        "assessmentSchedule": "string",
        "policyArn": "string",
        "creationTime": "timestamp",
        "lastAppComplianceEvaluationTime": "timestamp",
        "lastDriftEvaluationTime": "timestamp",
        "lastResiliencyScoreEvaluationTime": "timestamp",
        "tags": {},
        "permissionModel": {},
        "eventSubscriptions": []
    }
}
```

---

### 1.4 `list-apps`

Lists Resilience Hub applications. **Paginated.**

**Synopsis:**
```bash
aws resiliencehub list-apps \
    [--app-arn <value>] \
    [--name <value>] \
    [--from-last-assessment-time <value>] \
    [--to-last-assessment-time <value>] \
    [--reverse-order | --no-reverse-order] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | No | string | None | Filter by app ARN |
| `--name` | No | string | None | Filter by name |
| `--from-last-assessment-time` | No | timestamp | None | Filter by assessment time (from) |
| `--to-last-assessment-time` | No | timestamp | None | Filter by assessment time (to) |
| `--reverse-order` | No | boolean | None | Reverse sort order |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "appSummaries": [
        {
            "appArn": "string",
            "name": "string",
            "description": "string",
            "creationTime": "timestamp",
            "complianceStatus": "string",
            "resiliencyScore": "double",
            "assessmentSchedule": "string",
            "status": "string",
            "driftStatus": "string",
            "rtoInSecs": "integer",
            "rpoInSecs": "integer"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-app`

Updates a Resilience Hub application.

**Synopsis:**
```bash
aws resiliencehub update-app \
    --app-arn <value> \
    [--description <value>] \
    [--assessment-schedule <value>] \
    [--policy-arn <value>] \
    [--clear-resiliency-policy-arn | --no-clear-resiliency-policy-arn] \
    [--event-subscriptions <value>] \
    [--permission-model <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--description` | No | string | None | New description |
| `--assessment-schedule` | No | string | None | `Disabled` or `Daily` |
| `--policy-arn` | No | string | None | New policy ARN |
| `--clear-resiliency-policy-arn` | No | boolean | None | Clear attached policy |
| `--event-subscriptions` | No | list | None | Updated event subscriptions |
| `--permission-model` | No | structure | None | Updated permission model |

**Output Schema:**
```json
{
    "app": {
        "appArn": "string",
        "name": "string",
        "description": "string",
        "status": "string",
        "policyArn": "string",
        "assessmentSchedule": "string"
    }
}
```

---

### 1.6 `publish-app-version`

Publishes the draft version of a Resilience Hub application.

**Synopsis:**
```bash
aws resiliencehub publish-app-version \
    --app-arn <value> \
    [--version-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--version-name` | No | string | None | Version name |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "identifier": "integer",
    "versionName": "string"
}
```

---

### 1.7 `describe-app-version`

Describes a specific app version.

**Synopsis:**
```bash
aws resiliencehub describe-app-version \
    --app-arn <value> \
    --app-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-version` | **Yes** | string | -- | App version (e.g., `release`, `draft`) |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "additionalInfo": {"string": ["string"]},
    "identifier": "integer",
    "versionName": "string"
}
```

---

### 1.8 `list-app-versions`

Lists all versions of a Resilience Hub application. **Paginated.**

**Synopsis:**
```bash
aws resiliencehub list-app-versions \
    --app-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "appVersions": [
        {
            "appVersion": "string",
            "creationTime": "timestamp",
            "identifier": "integer",
            "versionName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.9 `update-app-version`

Updates an app version.

**Synopsis:**
```bash
aws resiliencehub update-app-version \
    --app-arn <value> \
    [--additional-info <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--additional-info` | No | map | None | Additional info. Shorthand: `KeyName1=string,string,KeyName2=string,string` |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "additionalInfo": {"string": ["string"]}
}
```
