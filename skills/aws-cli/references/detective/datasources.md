# Data Sources

### 4.1 `list-datasource-packages`

Lists the data source packages for a behavior graph. **Paginated operation.**

**Synopsis:**
```bash
aws detective list-datasource-packages \
    --graph-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DatasourcePackages": {
        "string": {
            "DatasourcePackageIngestState": "STARTED|STOPPED|DISABLED",
            "LastIngestStateChange": {
                "string": {
                    "Timestamp": "timestamp"
                }
            }
        }
    },
    "NextToken": "string"
}
```

---

### 4.2 `update-datasource-packages`

Starts a data source packages for a behavior graph.

**Synopsis:**
```bash
aws detective update-datasource-packages \
    --graph-arn <value> \
    --datasource-packages <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--datasource-packages` | **Yes** | list(string) | -- | Data source packages to enable: `DETECTIVE_CORE`, `EKS_AUDIT`, `ASFF_SECURITYHUB_FINDING` |

**Output:** None (HTTP 200 on success)

---

### 4.3 `batch-get-graph-member-datasources`

Gets data source information for a batch of member accounts in a behavior graph.

**Synopsis:**
```bash
aws detective batch-get-graph-member-datasources \
    --graph-arn <value> \
    --account-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arn` | **Yes** | string | -- | ARN of the behavior graph |
| `--account-ids` | **Yes** | list(string) | -- | Account IDs to get data source info for |

**Output Schema:**
```json
{
    "MemberDatasources": [
        {
            "AccountId": "string",
            "GraphArn": "string",
            "DatasourcePackageIngestHistory": {
                "string": {
                    "string": {
                        "Timestamp": "timestamp"
                    }
                }
            }
        }
    ],
    "UnprocessedAccounts": [
        {
            "AccountId": "string",
            "Reason": "string"
        }
    ]
}
```

---

### 4.4 `batch-get-membership-datasources`

Gets data source information for memberships from the calling account's perspective.

**Synopsis:**
```bash
aws detective batch-get-membership-datasources \
    --graph-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-arns` | **Yes** | list(string) | -- | Behavior graph ARNs to get data source info for |

**Output Schema:**
```json
{
    "MembershipDatasources": [
        {
            "AccountId": "string",
            "GraphArn": "string",
            "DatasourcePackageIngestHistory": {
                "string": {
                    "string": {
                        "Timestamp": "timestamp"
                    }
                }
            }
        }
    ],
    "UnprocessedGraphs": [
        {
            "GraphArn": "string",
            "Reason": "string"
        }
    ]
}
```
