# Privacy Budgets

## 7.1 `create-privacy-budget-template`

Creates a privacy budget template for a membership.

**Synopsis:**
```bash
aws cleanrooms create-privacy-budget-template \
    --membership-identifier <value> \
    --auto-refresh <value> \
    --privacy-budget-type <value> \
    --parameters <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--auto-refresh` | **Yes** | string | -- | Auto-refresh: `CALENDAR_MONTH` or `NONE` |
| `--privacy-budget-type` | **Yes** | string | -- | Budget type: `DIFFERENTIAL_PRIVACY` |
| `--parameters` | **Yes** | structure | -- | Budget parameters |
| `--tags` | No | map | None | Key-value tags |

**Parameters Structure (Differential Privacy):**
```json
{
    "differentialPrivacy": {
        "epsilon": 10,
        "usersNoisePerQuery": 30
    }
}
```

**Output Schema:**
```json
{
    "privacyBudgetTemplate": {
        "id": "string",
        "arn": "string",
        "membershipId": "string",
        "membershipArn": "string",
        "collaborationId": "string",
        "collaborationArn": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "privacyBudgetType": "DIFFERENTIAL_PRIVACY",
        "autoRefresh": "CALENDAR_MONTH|NONE",
        "parameters": {
            "differentialPrivacy": {
                "epsilon": "integer",
                "usersNoisePerQuery": "integer"
            }
        }
    }
}
```

---

## 7.2 `delete-privacy-budget-template`

Deletes a privacy budget template.

**Synopsis:**
```bash
aws cleanrooms delete-privacy-budget-template \
    --membership-identifier <value> \
    --privacy-budget-template-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--privacy-budget-template-identifier` | **Yes** | string | -- | Privacy budget template ID |

**Output Schema:**

None (HTTP 204 on success).

---

## 7.3 `get-privacy-budget-template`

Returns details for a privacy budget template.

**Synopsis:**
```bash
aws cleanrooms get-privacy-budget-template \
    --membership-identifier <value> \
    --privacy-budget-template-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--privacy-budget-template-identifier` | **Yes** | string | -- | Privacy budget template ID |

**Output Schema:**
```json
{
    "privacyBudgetTemplate": {
        "id": "string",
        "arn": "string",
        "membershipId": "string",
        "collaborationId": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "privacyBudgetType": "DIFFERENTIAL_PRIVACY",
        "autoRefresh": "string",
        "parameters": {}
    }
}
```

---

## 7.4 `list-privacy-budget-templates`

Lists privacy budget templates for a membership. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-privacy-budget-templates \
    --membership-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "privacyBudgetTemplateSummaries": [
        {
            "id": "string",
            "arn": "string",
            "membershipId": "string",
            "membershipArn": "string",
            "collaborationId": "string",
            "collaborationArn": "string",
            "privacyBudgetType": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 7.5 `list-privacy-budgets`

Lists privacy budgets for a membership. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-privacy-budgets \
    --membership-identifier <value> \
    --privacy-budget-type <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--privacy-budget-type` | **Yes** | string | -- | Budget type: `DIFFERENTIAL_PRIVACY` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "privacyBudgetSummaries": [
        {
            "id": "string",
            "privacyBudgetTemplateId": "string",
            "privacyBudgetTemplateArn": "string",
            "membershipId": "string",
            "collaborationId": "string",
            "collaborationArn": "string",
            "type": "DIFFERENTIAL_PRIVACY",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "budget": {
                "differentialPrivacy": {
                    "aggregations": [
                        {
                            "type": "AVG|COUNT|COUNT_DISTINCT|SUM|STDDEV",
                            "maxCount": "integer",
                            "remainingCount": "integer"
                        }
                    ],
                    "epsilon": "integer"
                }
            }
        }
    ],
    "nextToken": "string"
}
```

---

## 7.6 `update-privacy-budget-template`

Updates a privacy budget template.

**Synopsis:**
```bash
aws cleanrooms update-privacy-budget-template \
    --membership-identifier <value> \
    --privacy-budget-template-identifier <value> \
    --privacy-budget-type <value> \
    [--parameters <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--privacy-budget-template-identifier` | **Yes** | string | -- | Privacy budget template ID |
| `--privacy-budget-type` | **Yes** | string | -- | Budget type: `DIFFERENTIAL_PRIVACY` |
| `--parameters` | No | structure | None | Updated parameters |

**Output Schema:**
```json
{
    "privacyBudgetTemplate": {
        "id": "string",
        "arn": "string",
        "membershipId": "string",
        "collaborationId": "string",
        "updateTime": "timestamp",
        "parameters": {}
    }
}
```

---

## 7.7-7.9 Collaboration Privacy Budgets

`get-collaboration-privacy-budget-template`, `list-collaboration-privacy-budget-templates`, and `list-collaboration-privacy-budgets` follow the same pattern as membership-level operations but take `--collaboration-identifier` instead of `--membership-identifier`.

**Synopsis (get template):**
```bash
aws cleanrooms get-collaboration-privacy-budget-template \
    --collaboration-identifier <value> \
    --privacy-budget-template-identifier <value>
```

**Synopsis (list templates):**
```bash
aws cleanrooms list-collaboration-privacy-budget-templates \
    --collaboration-identifier <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

**Synopsis (list budgets):**
```bash
aws cleanrooms list-collaboration-privacy-budgets \
    --collaboration-identifier <value> \
    --privacy-budget-type DIFFERENTIAL_PRIVACY \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

---

## 7.10 `preview-privacy-impact`

Previews the privacy impact of a query before running it.

**Synopsis:**
```bash
aws cleanrooms preview-privacy-impact \
    --membership-identifier <value> \
    --parameters <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--parameters` | **Yes** | structure | -- | Query parameters to preview |

**Output Schema:**
```json
{
    "privacyImpact": {
        "differentialPrivacy": {
            "aggregations": [
                {
                    "type": "AVG|COUNT|COUNT_DISTINCT|SUM|STDDEV",
                    "maxCount": "integer",
                    "remainingCount": "integer"
                }
            ]
        }
    }
}
```

---

## 7.11 `tag-resource`

Adds tags to a Clean Rooms resource.

**Synopsis:**
```bash
aws cleanrooms tag-resource \
    --resource-arn <value> \
    --tags <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | map | -- | Key-value tags |

**Output Schema:**

None (HTTP 200 on success).

---

## 7.12 `untag-resource`

Removes tags from a Clean Rooms resource.

**Synopsis:**
```bash
aws cleanrooms untag-resource \
    --resource-arn <value> \
    --tag-keys <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**

None (HTTP 200 on success).

---

## 7.13 `list-tags-for-resource`

Lists tags for a Clean Rooms resource.

**Synopsis:**
```bash
aws cleanrooms list-tags-for-resource \
    --resource-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```
