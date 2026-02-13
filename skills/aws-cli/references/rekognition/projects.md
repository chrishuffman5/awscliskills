# Projects (Custom Labels)

### 8.1 `create-project`

Creates a Custom Labels project for training custom image classification or object detection models.

**Synopsis:**
```bash
aws rekognition create-project \
    --project-name <value> \
    [--feature <value>] \
    [--auto-update <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project name (1-255 chars) |
| `--feature` | No | string | `CUSTOM_LABELS` | Feature: `CONTENT_MODERATION` or `CUSTOM_LABELS` |
| `--auto-update` | No | string | -- | Auto-retraining: `ENABLED` or `DISABLED` |
| `--tags` | No | map | -- | Key-value tags (max 200) |

**Output Schema:**
```json
{
    "ProjectArn": "string"
}
```

---

### 8.2 `delete-project`

Deletes a project. Must delete all versions and datasets first.

**Synopsis:**
```bash
aws rekognition delete-project \
    --project-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the project to delete |

**Output Schema:**
```json
{
    "Status": "CREATING|CREATED|DELETING"
}
```

---

### 8.3 `describe-projects`

Lists and describes projects. **Paginated operation.**

**Synopsis:**
```bash
aws rekognition describe-projects \
    [--project-names <value>] \
    [--features <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-names` | No | list(string) | -- | Filter by project names (1-5) |
| `--features` | No | list(string) | -- | Filter by feature type |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "ProjectDescriptions": [
        {
            "ProjectArn": "string",
            "CreationTimestamp": "timestamp",
            "Status": "CREATING|CREATED|DELETING",
            "Datasets": [
                {
                    "CreationTimestamp": "timestamp",
                    "DatasetType": "TRAIN|TEST",
                    "DatasetArn": "string",
                    "Status": "CREATE_IN_PROGRESS|CREATE_COMPLETE|CREATE_FAILED|UPDATE_IN_PROGRESS|UPDATE_COMPLETE|UPDATE_FAILED_ROLLBACK_IN_PROGRESS|UPDATE_FAILED_ROLLBACK_COMPLETE|DELETE_IN_PROGRESS",
                    "StatusMessage": "string",
                    "StatusMessageCode": "string"
                }
            ],
            "Feature": "CONTENT_MODERATION|CUSTOM_LABELS",
            "AutoUpdate": "ENABLED|DISABLED"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.4 `create-project-version`

Trains a new version of a model using training and test datasets.

**Synopsis:**
```bash
aws rekognition create-project-version \
    --project-arn <value> \
    --version-name <value> \
    --output-config <value> \
    [--training-data <value>] \
    [--testing-data <value>] \
    [--tags <value>] \
    [--kms-key-id <value>] \
    [--version-description <value>] \
    [--feature-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the project |
| `--version-name` | **Yes** | string | -- | Version name (1-255 chars) |
| `--output-config` | **Yes** | structure | -- | S3 location for training output. Shorthand: `S3Bucket=string,S3KeyPrefix=string` |
| `--training-data` | No | structure | -- | Training dataset (assets array) |
| `--testing-data` | No | structure | -- | Testing dataset (assets array, auto-split percentage) |
| `--tags` | No | map | -- | Key-value tags |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--version-description` | No | string | -- | Description (1-255 chars) |
| `--feature-config` | No | structure | -- | Feature-specific config (e.g., content moderation confidence) |

**Output Schema:**
```json
{
    "ProjectVersionArn": "string"
}
```

---

### 8.5 `delete-project-version`

Deletes a model version. Must be stopped first.

**Synopsis:**
```bash
aws rekognition delete-project-version \
    --project-version-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-version-arn` | **Yes** | string | -- | ARN of the model version |

**Output Schema:**
```json
{
    "Status": "TRAINING_IN_PROGRESS|TRAINING_COMPLETED|TRAINING_FAILED|STARTING|RUNNING|FAILED|STOPPING|STOPPED|DELETING|COPYING_IN_PROGRESS|COPYING_COMPLETED|COPYING_FAILED|DEPRECATED|EXPIRED"
}
```

---

### 8.6 `describe-project-versions`

Describes model versions for a project. **Paginated operation.**

**Synopsis:**
```bash
aws rekognition describe-project-versions \
    --project-arn <value> \
    [--version-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 8.7 `copy-project-version`

Copies a model version to another project or region.

**Synopsis:**
```bash
aws rekognition copy-project-version \
    --source-project-arn <value> \
    --source-project-version-arn <value> \
    --destination-project-arn <value> \
    --version-name <value> \
    --output-config <value> \
    [--tags <value>] \
    [--kms-key-id <value>]
```

**Output Schema:**
```json
{
    "ProjectVersionArn": "string"
}
```

---

### 8.8 `start-project-version`

Starts (deploys) a trained model version for inference.

**Synopsis:**
```bash
aws rekognition start-project-version \
    --project-version-arn <value> \
    --min-inference-units <value> \
    [--max-inference-units <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-version-arn` | **Yes** | string | -- | ARN of the model version |
| `--min-inference-units` | **Yes** | integer | -- | Minimum inference units (min: 1) |
| `--max-inference-units` | No | integer | -- | Maximum inference units for auto-scaling |

**Output Schema:**
```json
{
    "Status": "string"
}
```

---

### 8.9 `stop-project-version`

Stops a running model version.

**Synopsis:**
```bash
aws rekognition stop-project-version \
    --project-version-arn <value>
```

**Output Schema:**
```json
{
    "Status": "string"
}
```

---

### 8.10 `detect-custom-labels`

Detects custom labels in an image using a running model version.

**Synopsis:**
```bash
aws rekognition detect-custom-labels \
    --project-version-arn <value> \
    [--image <value>] \
    [--image-bytes <value>] \
    [--max-results <value>] \
    [--min-confidence <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-version-arn` | **Yes** | string | -- | ARN of the running model version |
| `--image` | No* | structure | -- | Image as S3 object |
| `--image-bytes` | No* | blob | -- | Local file: `fileb://image.png` |
| `--max-results` | No | integer | -- | Maximum labels to return |
| `--min-confidence` | No | float | -- | Minimum confidence threshold (0-100) |

**Output Schema:**
```json
{
    "CustomLabels": [
        {
            "Name": "string",
            "Confidence": "float",
            "Geometry": {
                "BoundingBox": {},
                "Polygon": []
            }
        }
    ]
}
```

---

### 8.11 `put-project-policy`

Adds or updates a resource-based policy for a project.

**Synopsis:**
```bash
aws rekognition put-project-policy \
    --project-arn <value> \
    --policy-name <value> \
    --policy-document <value> \
    [--policy-revision-id <value>]
```

**Output Schema:**
```json
{
    "PolicyRevisionId": "string"
}
```

---

### 8.12 `delete-project-policy`

Deletes a resource-based policy from a project.

**Synopsis:**
```bash
aws rekognition delete-project-policy \
    --project-arn <value> \
    --policy-name <value> \
    [--policy-revision-id <value>]
```

**Output:** None (HTTP 200 on success)

---

### 8.13 `list-project-policies`

Lists resource-based policies for a project. **Paginated operation.**

**Synopsis:**
```bash
aws rekognition list-project-policies \
    --project-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "ProjectPolicies": [
        {
            "ProjectArn": "string",
            "PolicyName": "string",
            "PolicyRevisionId": "string",
            "PolicyDocument": "string",
            "CreationTimestamp": "timestamp",
            "LastUpdatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
