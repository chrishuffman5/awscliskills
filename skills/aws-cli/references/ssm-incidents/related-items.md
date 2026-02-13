# Related Items

### 4.1 `list-related-items`

List all related items for an incident record. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-incidents list-related-items \
    --incident-record-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--incident-record-arn` | **Yes** | string | -- | Incident record ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "relatedItems": [
        {
            "identifier": {
                "type": "ANALYSIS|INCIDENT|METRIC|PARENT|ATTACHMENT|OTHER|AUTOMATION|INVOLVED_RESOURCE|TASK",
                "value": {
                    "arn": "string",
                    "url": "string",
                    "metricDefinition": "string",
                    "pagerDutyIncidentDetail": {
                        "id": "string",
                        "autoResolve": "boolean"
                    }
                }
            },
            "title": "string",
            "generatedId": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.2 `update-related-items`

Add or remove related items from an incident record.

**Synopsis:**
```bash
aws ssm-incidents update-related-items \
    --incident-record-arn <value> \
    --related-items-update <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--incident-record-arn` | **Yes** | string | -- | Incident record ARN |
| `--related-items-update` | **Yes** | structure | -- | Update action (add or remove item) |
| `--client-token` | No | string | None | Idempotency token |

**Related Items Update Structure:**
```json
{
    "itemToAdd": {
        "identifier": {
            "type": "ANALYSIS|INCIDENT|METRIC|PARENT|ATTACHMENT|OTHER|AUTOMATION|INVOLVED_RESOURCE|TASK",
            "value": {
                "arn": "string",
                "url": "string"
            }
        },
        "title": "string"
    }
}
```
or
```json
{
    "itemToRemove": {
        "type": "string",
        "value": {
            "arn": "string",
            "url": "string"
        }
    }
}
```

**Output Schema:**
```json
{}
```
