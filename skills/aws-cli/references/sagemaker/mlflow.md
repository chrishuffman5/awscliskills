# MLflow

## 1. `create-mlflow-tracking-server`

Creates an MLflow tracking server for experiment tracking.

**Synopsis:**
```bash
aws sagemaker create-mlflow-tracking-server \
    --tracking-server-name <value> \
    --artifact-store-uri <value> \
    --role-arn <value> \
    [--tracking-server-size <value>] \
    [--mlflow-version <value>] \
    [--automatic-model-registration | --no-automatic-model-registration] \
    [--weekly-maintenance-window-start <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tracking-server-name` | **Yes** | string | -- | Server name (1-256 chars) |
| `--artifact-store-uri` | **Yes** | string | -- | S3 URI for artifacts |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--tracking-server-size` | No | string | `Small` | `Small`, `Medium`, `Large` |
| `--mlflow-version` | No | string | -- | MLflow version |
| `--automatic-model-registration` | No | boolean | false | Auto-register models |
| `--weekly-maintenance-window-start` | No | string | -- | Maintenance window (e.g., `Mon:01:00`) |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "TrackingServerArn": "string"
}
```

---

## 2. `describe-mlflow-tracking-server`

Returns details about an MLflow tracking server.

```bash
aws sagemaker describe-mlflow-tracking-server --tracking-server-name <value>
```

**Output Schema:**
```json
{
    "TrackingServerArn": "string",
    "TrackingServerName": "string",
    "ArtifactStoreUri": "string",
    "TrackingServerSize": "Small|Medium|Large",
    "MlflowVersion": "string",
    "RoleArn": "string",
    "TrackingServerStatus": "Creating|Created|CreateFailed|Updating|Updated|UpdateFailed|Deleting|DeleteFailed|Stopping|Stopped|StopFailed|Starting|Started|StartFailed|MaintenanceInProgress|MaintenanceComplete|MaintenanceFailed",
    "IsActive": "Active|Inactive",
    "TrackingServerUrl": "string",
    "WeeklyMaintenanceWindowStart": "string",
    "AutomaticModelRegistration": "boolean",
    "CreationTime": "timestamp",
    "CreatedBy": {...},
    "LastModifiedTime": "timestamp",
    "LastModifiedBy": {...}
}
```

---

## 3. `list-mlflow-tracking-servers`

Lists MLflow tracking servers. **Paginated operation.**

```bash
aws sagemaker list-mlflow-tracking-servers \
    [--created-after <value>] \
    [--created-before <value>] \
    [--tracking-server-status <value>] \
    [--mlflow-version <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

## 4. `update-mlflow-tracking-server`

Updates an MLflow tracking server.

```bash
aws sagemaker update-mlflow-tracking-server \
    --tracking-server-name <value> \
    [--artifact-store-uri <value>] \
    [--tracking-server-size <value>] \
    [--automatic-model-registration | --no-automatic-model-registration] \
    [--weekly-maintenance-window-start <value>]
```

**Output Schema:**
```json
{
    "TrackingServerArn": "string"
}
```

---

## 5. `start-mlflow-tracking-server` / `stop-mlflow-tracking-server` / `delete-mlflow-tracking-server`

```bash
aws sagemaker start-mlflow-tracking-server --tracking-server-name <value>
aws sagemaker stop-mlflow-tracking-server --tracking-server-name <value>
aws sagemaker delete-mlflow-tracking-server --tracking-server-name <value>
```

---

## 6. `create-presigned-mlflow-tracking-server-url`

Creates a presigned URL for accessing the MLflow UI.

```bash
aws sagemaker create-presigned-mlflow-tracking-server-url \
    --tracking-server-name <value> \
    [--expires-in-seconds <value>] \
    [--session-expiration-duration-in-seconds <value>]
```

**Output Schema:**
```json
{
    "AuthorizedUrl": "string"
}
```

---

## MLflow Apps

### 7. `create-mlflow-app` / `describe-mlflow-app` / `list-mlflow-apps` / `update-mlflow-app` / `delete-mlflow-app`

```bash
aws sagemaker create-mlflow-app --app-name <value> --tracking-server-name <value> [--tags <value>]
aws sagemaker describe-mlflow-app --app-name <value>
aws sagemaker list-mlflow-apps [--starting-token <value>] [--page-size <value>] [--max-items <value>]
aws sagemaker update-mlflow-app --app-name <value> [--tracking-server-name <value>]
aws sagemaker delete-mlflow-app --app-name <value>
```

### 8. `create-presigned-mlflow-app-url`

Creates a presigned URL for accessing an MLflow app.

```bash
aws sagemaker create-presigned-mlflow-app-url \
    --app-name <value> \
    [--expires-in-seconds <value>] \
    [--session-expiration-duration-in-seconds <value>]
```

**Output Schema:**
```json
{
    "AuthorizedUrl": "string"
}
```
