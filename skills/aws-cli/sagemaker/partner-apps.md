# Partner Apps

## 1. `create-partner-app`

Creates a SageMaker partner app integration.

**Synopsis:**
```bash
aws sagemaker create-partner-app \
    --name <value> \
    --type <value> \
    --execution-role-arn <value> \
    [--maintenance-config <value>] \
    [--tier <value>] \
    [--application-config <value>] \
    [--auth-type <value>] \
    [--enable-iam-session-based-identity | --no-enable-iam-session-based-identity] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | App name |
| `--type` | **Yes** | string | -- | `lakera-guard`, `comet`, `deepchecks-llm-evaluation`, `fiddler` |
| `--execution-role-arn` | **Yes** | string | -- | IAM role ARN |
| `--maintenance-config` | No | structure | -- | `MaintenanceWindowStart` |
| `--tier` | No | string | -- | App tier |
| `--application-config` | No | structure | -- | App-specific admin config |
| `--auth-type` | No | string | -- | `IAM` |
| `--enable-iam-session-based-identity` | No | boolean | -- | Enable IAM session identity |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

## 2. `describe-partner-app`

Returns details about a partner app.

```bash
aws sagemaker describe-partner-app --arn <value>
```

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "Type": "lakera-guard|comet|deepchecks-llm-evaluation|fiddler",
    "Status": "Creating|Updating|Deleting|Available|Failed|UpdateFailed|DeleteFailed",
    "CreationTime": "timestamp",
    "ExecutionRoleArn": "string",
    "BaseUrl": "string",
    "MaintenanceConfig": {"MaintenanceWindowStart": "string"},
    "Tier": "string",
    "Version": "string",
    "ApplicationConfig": {...},
    "AuthType": "IAM",
    "EnableIamSessionBasedIdentity": "boolean",
    "Error": {"ErrorCode": "string", "ErrorMessage": "string"}
}
```

---

## 3. `list-partner-apps`

Lists partner apps. **Paginated operation.**

```bash
aws sagemaker list-partner-apps \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

## 4. `update-partner-app`

Updates a partner app.

```bash
aws sagemaker update-partner-app \
    --arn <value> \
    [--maintenance-config <value>] \
    [--tier <value>] \
    [--application-config <value>] \
    [--enable-iam-session-based-identity | --no-enable-iam-session-based-identity] \
    [--client-token <value>] \
    [--tags <value>]
```

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

## 5. `delete-partner-app`

Deletes a partner app.

```bash
aws sagemaker delete-partner-app --arn <value> [--client-token <value>]
```

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

## 6. `create-partner-app-presigned-url`

Creates a presigned URL for accessing a partner app.

```bash
aws sagemaker create-partner-app-presigned-url \
    --arn <value> \
    [--expires-in-seconds <value>]
```

**Output Schema:**
```json
{
    "Url": "string"
}
```
