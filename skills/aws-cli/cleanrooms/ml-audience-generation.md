# ML Audience Generation

> Commands in this file use the `aws cleanroomsml` namespace.

## 15.1 `start-audience-generation-job`

Starts an audience generation job using a configured audience model.

**Synopsis:**
```bash
aws cleanroomsml start-audience-generation-job \
    --name <value> \
    --configured-audience-model-arn <value> \
    --seed-audience <value> \
    [--collaboration-id <value>] \
    [--include-seed-in-output | --no-include-seed-in-output] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Job name |
| `--configured-audience-model-arn` | **Yes** | string | -- | Configured audience model ARN |
| `--seed-audience` | **Yes** | structure | -- | Seed audience data source |
| `--collaboration-id` | No | string | None | Collaboration ID |
| `--include-seed-in-output` | No | boolean | None | Include seed users in output |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Key-value tags |

**Seed Audience Structure:**
```json
{
    "DataSource": {
        "S3Uri": "s3://seed-bucket/seed-data.csv"
    },
    "RoleArn": "arn:aws:iam::123456789012:role/SeedDataRole"
}
```

**Output Schema:**
```json
{
    "audienceGenerationJobArn": "string"
}
```

---

## 15.2 `delete-audience-generation-job`

Deletes an audience generation job.

**Synopsis:**
```bash
aws cleanroomsml delete-audience-generation-job \
    --audience-generation-job-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--audience-generation-job-arn` | **Yes** | string | -- | Audience generation job ARN |

**Output Schema:**

None (HTTP 200 on success).

---

## 15.3 `get-audience-generation-job`

Returns details for an audience generation job.

**Synopsis:**
```bash
aws cleanroomsml get-audience-generation-job \
    --audience-generation-job-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--audience-generation-job-arn` | **Yes** | string | -- | Job ARN |

**Output Schema:**
```json
{
    "createTime": "timestamp",
    "updateTime": "timestamp",
    "audienceGenerationJobArn": "string",
    "name": "string",
    "description": "string",
    "status": "CREATE_PENDING|CREATE_IN_PROGRESS|CREATE_FAILED|ACTIVE|DELETE_PENDING|DELETE_IN_PROGRESS|DELETE_FAILED",
    "statusDetails": {},
    "configuredAudienceModelArn": "string",
    "seedAudience": {
        "dataSource": { "s3Uri": "string" },
        "roleArn": "string"
    },
    "includeSeedInOutput": "boolean",
    "collaborationId": "string",
    "metrics": {
        "relevanceMetrics": [
            {
                "audienceSize": {
                    "type": "ABSOLUTE|PERCENTAGE",
                    "value": "integer"
                },
                "score": "double"
            }
        ]
    },
    "startedBy": "string",
    "tags": { "string": "string" },
    "protectedQueryIdentifier": "string"
}
```

---

## 15.4 `list-audience-generation-jobs`

Lists audience generation jobs. **Paginated operation.**

**Synopsis:**
```bash
aws cleanroomsml list-audience-generation-jobs \
    [--configured-audience-model-arn <value>] \
    [--collaboration-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "audienceGenerationJobs": [
        {
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "audienceGenerationJobArn": "string",
            "name": "string",
            "description": "string",
            "status": "string",
            "configuredAudienceModelArn": "string",
            "collaborationId": "string",
            "startedBy": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 15.5 `start-audience-export-job`

Starts an audience export job to export generated audience data.

**Synopsis:**
```bash
aws cleanroomsml start-audience-export-job \
    --name <value> \
    --audience-generation-job-arn <value> \
    --audience-size <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Export job name |
| `--audience-generation-job-arn` | **Yes** | string | -- | Audience generation job ARN |
| `--audience-size` | **Yes** | structure | -- | Audience size. Shorthand: `type=ABSOLUTE\|PERCENTAGE,value=integer` |
| `--description` | No | string | None | Description |

**Output Schema:**

None (HTTP 200 on success).

---

## 15.6 `list-audience-export-jobs`

Lists audience export jobs. **Paginated operation.**

**Synopsis:**
```bash
aws cleanroomsml list-audience-export-jobs \
    [--audience-generation-job-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "audienceExportJobs": [
        {
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "name": "string",
            "audienceGenerationJobArn": "string",
            "audienceSize": {
                "type": "ABSOLUTE|PERCENTAGE",
                "value": "integer"
            },
            "description": "string",
            "status": "CREATE_PENDING|CREATE_IN_PROGRESS|CREATE_FAILED|ACTIVE",
            "statusDetails": {},
            "outputLocation": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 15.7 `delete-configured-audience-model-policy`

Deletes a configured audience model resource policy.

**Synopsis:**
```bash
aws cleanroomsml delete-configured-audience-model-policy \
    --configured-audience-model-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-audience-model-arn` | **Yes** | string | -- | Configured audience model ARN |

**Output Schema:**

None (HTTP 200 on success).

---

## 15.8 `get-configured-audience-model-policy`

Returns the resource policy for a configured audience model.

**Synopsis:**
```bash
aws cleanroomsml get-configured-audience-model-policy \
    --configured-audience-model-arn <value>
```

**Output Schema:**
```json
{
    "configuredAudienceModelArn": "string",
    "configuredAudienceModelPolicy": "string",
    "policyHash": "string"
}
```

---

## 15.9 `put-configured-audience-model-policy`

Sets a resource policy for a configured audience model.

**Synopsis:**
```bash
aws cleanroomsml put-configured-audience-model-policy \
    --configured-audience-model-arn <value> \
    --configured-audience-model-policy <value> \
    [--previous-policy-hash <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configured-audience-model-arn` | **Yes** | string | -- | Configured audience model ARN |
| `--configured-audience-model-policy` | **Yes** | string | -- | Policy JSON string |
| `--previous-policy-hash` | No | string | None | Previous policy hash for optimistic locking |

**Output Schema:**
```json
{
    "configuredAudienceModelPolicy": "string",
    "policyHash": "string"
}
```

---

## 15.10 `delete-ml-configuration`

Deletes the ML configuration for a membership.

**Synopsis:**
```bash
aws cleanroomsml delete-ml-configuration \
    --membership-identifier <value>
```

**Output Schema:**

None (HTTP 200 on success).

---

## 15.11 `get-ml-configuration`

Returns the ML configuration for a membership.

**Synopsis:**
```bash
aws cleanroomsml get-ml-configuration \
    --membership-identifier <value>
```

**Output Schema:**
```json
{
    "membershipIdentifier": "string",
    "defaultOutputLocation": {
        "destination": {
            "s3Destination": {
                "s3Uri": "string"
            }
        },
        "roleArn": "string"
    },
    "createTime": "timestamp",
    "updateTime": "timestamp"
}
```

---

## 15.12 `put-ml-configuration`

Sets the ML configuration for a membership.

**Synopsis:**
```bash
aws cleanroomsml put-ml-configuration \
    --membership-identifier <value> \
    --default-output-location <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--default-output-location` | **Yes** | structure | -- | Default output location |

**Output Schema:**

None (HTTP 200 on success).

---

## 15.13 `tag-resource` / `untag-resource` / `list-tags-for-resource`

Standard tagging operations for Clean Rooms ML resources. Same signature as `aws cleanrooms` tag operations.

**Synopsis:**
```bash
aws cleanroomsml tag-resource --resource-arn <value> --tags <value>
aws cleanroomsml untag-resource --resource-arn <value> --tag-keys <value>
aws cleanroomsml list-tags-for-resource --resource-arn <value>
```
