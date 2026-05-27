# Campaigns

### 5.1 `create-campaign`

Deploys a trained solution version (model) as a real-time campaign endpoint for serving recommendations.

**Synopsis:**
```bash
aws personalize create-campaign \
    --name <value> \
    --solution-version-arn <value> \
    [--min-provisioned-tps <value>] \
    [--campaign-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Campaign name (1-63 chars) |
| `--solution-version-arn` | **Yes** | string | -- | ARN of the solution version to deploy |
| `--min-provisioned-tps` | No | integer | 1 | Minimum provisioned transactions per second |
| `--campaign-config` | No | structure | None | Campaign configuration (exploration, metadata, auto-sync) |
| `--tags` | No | list | None | Tags (max 200) |

**CampaignConfig Structure:**
```json
{
    "itemExplorationConfig": {"string": "string"},
    "enableMetadataWithRecommendations": true|false,
    "syncWithLatestSolutionVersion": true|false
}
```

**Output Schema:**
```json
{
    "campaignArn": "string"
}
```

---

### 5.2 `describe-campaign`

Describes a campaign.

**Synopsis:**
```bash
aws personalize describe-campaign \
    --campaign-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--campaign-arn` | **Yes** | string | -- | ARN of the campaign |

**Output Schema:**
```json
{
    "campaign": {
        "name": "string",
        "campaignArn": "string",
        "solutionVersionArn": "string",
        "minProvisionedTPS": "integer",
        "campaignConfig": {
            "itemExplorationConfig": {},
            "enableMetadataWithRecommendations": true|false,
            "syncWithLatestSolutionVersion": true|false
        },
        "status": "string",
        "failureReason": "string",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp",
        "latestCampaignUpdate": {
            "solutionVersionArn": "string",
            "minProvisionedTPS": "integer",
            "campaignConfig": {},
            "status": "string",
            "failureReason": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp"
        }
    }
}
```

---

### 5.3 `list-campaigns`

Lists campaigns for a solution. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-campaigns \
    [--solution-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--solution-arn` | No | string | None | Filter by solution ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "campaigns": [
        {
            "name": "string",
            "campaignArn": "string",
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "failureReason": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.4 `update-campaign`

Updates a campaign to deploy a new solution version or change provisioned throughput.

**Synopsis:**
```bash
aws personalize update-campaign \
    --campaign-arn <value> \
    [--solution-version-arn <value>] \
    [--min-provisioned-tps <value>] \
    [--campaign-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--campaign-arn` | **Yes** | string | -- | ARN of the campaign to update |
| `--solution-version-arn` | No | string | None | New solution version ARN |
| `--min-provisioned-tps` | No | integer | None | Updated provisioned TPS |
| `--campaign-config` | No | structure | None | Updated campaign configuration |

**Output Schema:**
```json
{
    "campaignArn": "string"
}
```

---

### 5.5 `delete-campaign`

Deletes a campaign. Cannot delete while status is `CREATE PENDING` or `IN_PROGRESS`.

**Synopsis:**
```bash
aws personalize delete-campaign \
    --campaign-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--campaign-arn` | **Yes** | string | -- | ARN of the campaign to delete |

**Output:** None
