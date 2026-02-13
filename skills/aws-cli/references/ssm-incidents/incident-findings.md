# Incident Findings

### 3.1 `batch-get-incident-findings`

Retrieves details about all specified findings for an incident, including the contributors to each finding.

**Synopsis:**
```bash
aws ssm-incidents batch-get-incident-findings \
    --incident-record-arn <value> \
    --finding-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--incident-record-arn` | **Yes** | string | -- | Incident record ARN |
| `--finding-ids` | **Yes** | list(string) | -- | Finding IDs to retrieve |

**Output Schema:**
```json
{
    "findings": [
        {
            "id": "string",
            "creationTime": "timestamp",
            "lastModifiedTime": "timestamp",
            "details": {
                "cloudFormationStackUpdate": {
                    "startTime": "timestamp",
                    "endTime": "timestamp",
                    "stackArn": "string"
                },
                "codeDeployDeployment": {
                    "startTime": "timestamp",
                    "endTime": "timestamp",
                    "deploymentGroupArn": "string",
                    "deploymentId": "string"
                }
            }
        }
    ],
    "errors": [
        {
            "code": "string",
            "message": "string"
        }
    ]
}
```

---

### 3.2 `list-incident-findings`

Retrieves a list of the IDs of findings, plus their last modified times, that have been identified for a specified incident. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-incidents list-incident-findings \
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
    "findings": [
        {
            "id": "string",
            "lastModifiedTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
