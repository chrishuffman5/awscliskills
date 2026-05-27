# Workloads

### 1.1 `create-workload`

Creates a new workload for review in the Well-Architected Framework.

**Synopsis:**
```bash
aws wellarchitected create-workload \
    --workload-name <value> \
    --description <value> \
    --environment <value> \
    --lenses <value> \
    [--account-ids <value>] \
    [--aws-regions <value>] \
    [--non-aws-regions <value>] \
    [--pillar-priorities <value>] \
    [--architectural-design <value>] \
    [--review-owner <value>] \
    [--industry-type <value>] \
    [--industry <value>] \
    [--notes <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--discovery-config <value>] \
    [--applications <value>] \
    [--profile-arns <value>] \
    [--review-template-arns <value>] \
    [--jira-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-name` | **Yes** | string | -- | Workload name (3-100 chars, unique per account/region) |
| `--description` | **Yes** | string | -- | Description (3-250 chars) |
| `--environment` | **Yes** | string | -- | `PRODUCTION` or `PREPRODUCTION` |
| `--lenses` | **Yes** | list(string) | -- | Lens aliases or ARNs (e.g., `wellarchitected`, `serverless`) |
| `--account-ids` | No | list(string) | None | Associated AWS account IDs (max 100) |
| `--aws-regions` | No | list(string) | None | AWS regions (max 50) |
| `--non-aws-regions` | No | list(string) | None | Non-AWS regions (max 5) |
| `--pillar-priorities` | No | list(string) | None | Pillar IDs for ordering improvement plans |
| `--architectural-design` | No | string | None | URL of architectural design (max 2048 chars) |
| `--review-owner` | No | string | None | Review process owner (3-255 chars) |
| `--industry-type` | No | string | None | Industry type (max 100 chars) |
| `--industry` | No | string | None | Industry classification (max 100 chars) |
| `--notes` | No | string | None | Notes (max 2084 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token (1-2048 chars) |
| `--tags` | No | map | None | Tags (1-50 tags) |
| `--discovery-config` | No | structure | None | Discovery config (JSON) |
| `--applications` | No | list(string) | None | AppRegistry ARNs (max 1) |
| `--profile-arns` | No | list(string) | None | Profile ARNs (max 1) |
| `--review-template-arns` | No | list(string) | None | Review template ARNs (max 1) |
| `--jira-configuration` | No | structure | None | Jira config. Shorthand: `IssueManagementStatus=ENABLED\|DISABLED,IssueManagementType=AUTO\|MANUAL,JiraProjectKey=string` |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "WorkloadArn": "string"
}
```

---

### 1.2 `delete-workload`

Deletes a workload. Only the workload owner can delete it.

**Synopsis:**
```bash
aws wellarchitected delete-workload \
    --workload-id <value> \
    --client-request-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID (32 hex chars) |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
None
```

---

### 1.3 `get-workload`

Retrieves workload properties.

**Synopsis:**
```bash
aws wellarchitected get-workload \
    --workload-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID (32 hex chars) |

**Output Schema:**
```json
{
    "Workload": {
        "WorkloadId": "string",
        "WorkloadArn": "string",
        "WorkloadName": "string",
        "Description": "string",
        "Environment": "PRODUCTION|PREPRODUCTION",
        "UpdatedAt": "timestamp",
        "AccountIds": ["string"],
        "AwsRegions": ["string"],
        "NonAwsRegions": ["string"],
        "ArchitecturalDesign": "string",
        "ReviewOwner": "string",
        "ReviewRestrictionDate": "timestamp",
        "IsReviewOwnerUpdateAcknowledged": "boolean",
        "IndustryType": "string",
        "Industry": "string",
        "Notes": "string",
        "ImprovementStatus": "NOT_APPLICABLE|NOT_STARTED|IN_PROGRESS|COMPLETE|RISK_ACKNOWLEDGED",
        "RiskCounts": {
            "UNANSWERED": "integer",
            "HIGH": "integer",
            "MEDIUM": "integer",
            "NONE": "integer",
            "NOT_APPLICABLE": "integer"
        },
        "PillarPriorities": ["string"],
        "Lenses": ["string"],
        "Owner": "string",
        "ShareInvitationId": "string",
        "Tags": {"string": "string"},
        "DiscoveryConfig": {
            "TrustedAdvisorIntegrationStatus": "ENABLED|DISABLED",
            "WorkloadResourceDefinition": ["WORKLOAD_METADATA|APP_REGISTRY"]
        },
        "Applications": ["string"],
        "Profiles": [{"ProfileArn": "string", "ProfileVersion": "string"}],
        "PrioritizedRiskCounts": {},
        "JiraConfiguration": {}
    }
}
```

---

### 1.4 `list-workloads`

Lists all workloads in the account. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-workloads \
    [--workload-name-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-name-prefix` | No | string | None | Filter by name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 50) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "WorkloadSummaries": [
        {
            "WorkloadId": "string",
            "WorkloadArn": "string",
            "WorkloadName": "string",
            "Owner": "string",
            "UpdatedAt": "timestamp",
            "Lenses": ["string"],
            "RiskCounts": {},
            "ImprovementStatus": "string",
            "Profiles": [],
            "PrioritizedRiskCounts": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-workload`

Updates workload properties.

**Synopsis:**
```bash
aws wellarchitected update-workload \
    --workload-id <value> \
    [--workload-name <value>] \
    [--description <value>] \
    [--environment <value>] \
    [--account-ids <value>] \
    [--aws-regions <value>] \
    [--non-aws-regions <value>] \
    [--pillar-priorities <value>] \
    [--architectural-design <value>] \
    [--review-owner <value>] \
    [--is-review-owner-update-acknowledged | --no-is-review-owner-update-acknowledged] \
    [--industry-type <value>] \
    [--industry <value>] \
    [--notes <value>] \
    [--improvement-status <value>] \
    [--discovery-config <value>] \
    [--applications <value>] \
    [--jira-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--workload-name` | No | string | None | New name |
| `--description` | No | string | None | New description |
| `--environment` | No | string | None | `PRODUCTION` or `PREPRODUCTION` |
| `--account-ids` | No | list(string) | None | Updated account IDs |
| `--aws-regions` | No | list(string) | None | Updated regions |
| `--non-aws-regions` | No | list(string) | None | Updated non-AWS regions |
| `--pillar-priorities` | No | list(string) | None | Updated pillar priorities |
| `--architectural-design` | No | string | None | Updated architecture URL |
| `--review-owner` | No | string | None | Updated review owner |
| `--is-review-owner-update-acknowledged` | No | boolean | None | Acknowledge review owner change |
| `--industry-type` | No | string | None | Updated industry type |
| `--industry` | No | string | None | Updated industry |
| `--notes` | No | string | None | Updated notes |
| `--improvement-status` | No | string | None | `NOT_APPLICABLE`, `NOT_STARTED`, `IN_PROGRESS`, `COMPLETE`, `RISK_ACKNOWLEDGED` |
| `--discovery-config` | No | structure | None | Updated discovery config |
| `--applications` | No | list(string) | None | Updated applications |
| `--jira-configuration` | No | structure | None | Updated Jira config |

**Output Schema:**
```json
{
    "Workload": {
        "WorkloadId": "string",
        "WorkloadArn": "string",
        "WorkloadName": "string",
        "Description": "string",
        "Environment": "string",
        "UpdatedAt": "timestamp"
    }
}
```

---

### 1.6 `create-workload-share`

Shares a workload with another AWS account, user, organization, or OU.

**Synopsis:**
```bash
aws wellarchitected create-workload-share \
    --workload-id <value> \
    --shared-with <value> \
    --permission-type <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--shared-with` | **Yes** | string | -- | Account ID, IAM user ARN, org ID, or OU ID (12-2048 chars) |
| `--permission-type` | **Yes** | string | -- | `READONLY` or `CONTRIBUTOR` |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "ShareId": "string"
}
```

---

### 1.7 `delete-workload-share`

Deletes a workload share.

**Synopsis:**
```bash
aws wellarchitected delete-workload-share \
    --share-id <value> \
    --workload-id <value> \
    --client-request-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--share-id` | **Yes** | string | -- | Share ID |
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
None
```

---

### 1.8 `list-workload-shares`

Lists shares for a workload. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-workload-shares \
    --workload-id <value> \
    [--shared-with-prefix <value>] \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--shared-with-prefix` | No | string | None | Filter by shared-with prefix |
| `--status` | No | string | None | `ACCEPTED`, `REJECTED`, `PENDING`, `REVOKED`, `EXPIRED`, `ASSOCIATING`, `ASSOCIATED`, `FAILED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "WorkloadShareSummaries": [
        {
            "ShareId": "string",
            "SharedWith": "string",
            "PermissionType": "READONLY|CONTRIBUTOR",
            "Status": "string",
            "StatusMessage": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.9 `update-workload-share`

Updates a workload share permission.

**Synopsis:**
```bash
aws wellarchitected update-workload-share \
    --share-id <value> \
    --workload-id <value> \
    --permission-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--share-id` | **Yes** | string | -- | Share ID |
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--permission-type` | **Yes** | string | -- | `READONLY` or `CONTRIBUTOR` |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "WorkloadShare": {
        "ShareId": "string",
        "SharedWith": "string",
        "PermissionType": "READONLY|CONTRIBUTOR",
        "Status": "string"
    }
}
```
