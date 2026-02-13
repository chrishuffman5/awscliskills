# Experiments

## 1. `create-experiment`

Creates an experiment for organizing and tracking ML iterations.

**Synopsis:**
```bash
aws sagemaker create-experiment \
    --experiment-name <value> \
    [--display-name <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-name` | **Yes** | string | -- | Unique name (1-120 chars) |
| `--display-name` | No | string | -- | Display name (1-120 chars) |
| `--description` | No | string | -- | Description (max 3072 chars) |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "ExperimentArn": "string"
}
```

---

## 2. `describe-experiment`

Returns information about an experiment.

**Synopsis:**
```bash
aws sagemaker describe-experiment \
    --experiment-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-name` | **Yes** | string | -- | Experiment name |

**Output Schema:**
```json
{
    "ExperimentName": "string",
    "ExperimentArn": "string",
    "DisplayName": "string",
    "Source": {"SourceArn": "string", "SourceType": "string"},
    "Description": "string",
    "CreationTime": "timestamp",
    "CreatedBy": {"UserProfileArn": "string", "UserProfileName": "string", "DomainId": "string"},
    "LastModifiedTime": "timestamp",
    "LastModifiedBy": {...}
}
```

---

## 3. `list-experiments`

Lists experiments. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-experiments \
    [--created-after <value>] \
    [--created-before <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--created-after` | No | timestamp | -- | Filter by creation time |
| `--created-before` | No | timestamp | -- | Filter by creation time |
| `--sort-by` | No | string | `Name` | `Name`, `CreationTime` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "ExperimentSummaries": [
        {
            "ExperimentArn": "string",
            "ExperimentName": "string",
            "DisplayName": "string",
            "ExperimentSource": {"SourceArn": "string", "SourceType": "string"},
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 4. `update-experiment`

Updates an experiment.

**Synopsis:**
```bash
aws sagemaker update-experiment \
    --experiment-name <value> \
    [--display-name <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-name` | **Yes** | string | -- | Experiment name |
| `--display-name` | No | string | -- | Updated display name |
| `--description` | No | string | -- | Updated description |

**Output Schema:**
```json
{
    "ExperimentArn": "string"
}
```

---

## 5. `delete-experiment`

Deletes an experiment. All trials in the experiment must be deleted first.

**Synopsis:**
```bash
aws sagemaker delete-experiment \
    --experiment-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-name` | **Yes** | string | -- | Experiment name |

**Output Schema:**
```json
{
    "ExperimentArn": "string"
}
```

---

## 6. `create-trial`

Creates a trial within an experiment.

**Synopsis:**
```bash
aws sagemaker create-trial \
    --trial-name <value> \
    --experiment-name <value> \
    [--display-name <value>] \
    [--metadata-properties <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trial-name` | **Yes** | string | -- | Unique trial name (1-120 chars) |
| `--experiment-name` | **Yes** | string | -- | Parent experiment name |
| `--display-name` | No | string | -- | Display name |
| `--metadata-properties` | No | structure | -- | `CommitId`, `Repository`, `GeneratedBy`, `ProjectId` |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "TrialArn": "string"
}
```

---

## 7. `describe-trial`

Returns information about a trial.

**Synopsis:**
```bash
aws sagemaker describe-trial \
    --trial-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trial-name` | **Yes** | string | -- | Trial name |

**Output Schema:**
```json
{
    "TrialName": "string",
    "TrialArn": "string",
    "DisplayName": "string",
    "ExperimentName": "string",
    "Source": {"SourceArn": "string", "SourceType": "string"},
    "CreationTime": "timestamp",
    "CreatedBy": {...},
    "LastModifiedTime": "timestamp",
    "LastModifiedBy": {...},
    "MetadataProperties": {"CommitId": "string", "Repository": "string", "GeneratedBy": "string", "ProjectId": "string"}
}
```

---

## 8. `list-trials`

Lists trials. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-trials \
    [--experiment-name <value>] \
    [--trial-component-name <value>] \
    [--created-after <value>] \
    [--created-before <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-name` | No | string | -- | Filter by experiment |
| `--trial-component-name` | No | string | -- | Filter by trial component |
| `--sort-by` | No | string | `Name` | `Name`, `CreationTime` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "TrialSummaries": [
        {
            "TrialArn": "string",
            "TrialName": "string",
            "DisplayName": "string",
            "TrialSource": {"SourceArn": "string", "SourceType": "string"},
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 9. `update-trial` / `delete-trial`

Update or delete a trial.

**Synopsis:**
```bash
aws sagemaker update-trial --trial-name <value> [--display-name <value>]
aws sagemaker delete-trial --trial-name <value>
```

---

## 10. `create-trial-component`

Creates a trial component (a stage of a trial, such as training or evaluation).

**Synopsis:**
```bash
aws sagemaker create-trial-component \
    --trial-component-name <value> \
    [--display-name <value>] \
    [--status <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--parameters <value>] \
    [--input-artifacts <value>] \
    [--output-artifacts <value>] \
    [--metadata-properties <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trial-component-name` | **Yes** | string | -- | Unique name (1-120 chars) |
| `--display-name` | No | string | -- | Display name |
| `--status` | No | structure | -- | `PrimaryStatus` (`InProgress`/`Completed`/`Failed`/`Stopping`/`Stopped`), `Message` |
| `--start-time` | No | timestamp | -- | Start time |
| `--end-time` | No | timestamp | -- | End time |
| `--parameters` | No | map | -- | Key-value parameter map |
| `--input-artifacts` | No | map | -- | Input artifacts (`Value`, `MediaType`) |
| `--output-artifacts` | No | map | -- | Output artifacts (`Value`, `MediaType`) |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "TrialComponentArn": "string"
}
```

---

## 11. `describe-trial-component`

Returns information about a trial component.

**Synopsis:**
```bash
aws sagemaker describe-trial-component \
    --trial-component-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trial-component-name` | **Yes** | string | -- | Trial component name |

**Output Schema:**
```json
{
    "TrialComponentName": "string",
    "TrialComponentArn": "string",
    "DisplayName": "string",
    "Source": {"SourceArn": "string", "SourceType": "string"},
    "Status": {"PrimaryStatus": "string", "Message": "string"},
    "StartTime": "timestamp",
    "EndTime": "timestamp",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "Parameters": {"string": {"StringValue": "string", "NumberValue": "double"}},
    "InputArtifacts": {"string": {"Value": "string", "MediaType": "string"}},
    "OutputArtifacts": {"string": {"Value": "string", "MediaType": "string"}},
    "MetadataProperties": {...},
    "Metrics": [{"MetricName": "string", "SourceArn": "string", "TimeStamp": "timestamp", "Max": "double", "Min": "double", "Last": "double", "Count": "integer", "Avg": "double", "StdDev": "double"}],
    "LineageGroupArn": "string",
    "Sources": [{"SourceArn": "string", "SourceType": "string"}]
}
```

---

## 12. `list-trial-components`

Lists trial components. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-trial-components \
    [--experiment-name <value>] \
    [--trial-name <value>] \
    [--source-arn <value>] \
    [--created-after <value>] \
    [--created-before <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

## 13. `associate-trial-component`

Associates a trial component with a trial.

**Synopsis:**
```bash
aws sagemaker associate-trial-component \
    --trial-component-name <value> \
    --trial-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trial-component-name` | **Yes** | string | -- | Trial component name |
| `--trial-name` | **Yes** | string | -- | Trial name |

**Output Schema:**
```json
{
    "TrialComponentArn": "string",
    "TrialArn": "string"
}
```

---

## 14. `disassociate-trial-component`

Disassociates a trial component from a trial.

**Synopsis:**
```bash
aws sagemaker disassociate-trial-component \
    --trial-component-name <value> \
    --trial-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trial-component-name` | **Yes** | string | -- | Trial component name |
| `--trial-name` | **Yes** | string | -- | Trial name |

**Output Schema:**
```json
{
    "TrialComponentArn": "string",
    "TrialArn": "string"
}
```
