# Image Scanning

### 6.1 `list-image-scan-findings`

Lists image scan findings. Returns vulnerability findings from image scans. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-image-scan-findings \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters for findings. Shorthand: `name=string,values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Names:**
- `imageBuildVersionArn` - Filter by image build version ARN
- `imagePipelineArn` - Filter by image pipeline ARN
- `vulnerabilityId` - Filter by vulnerability ID

**Output Schema:**
```json
{
    "requestId": "string",
    "findings": [
        {
            "awsAccountId": "string",
            "imageBuildVersionArn": "string",
            "imagePipelineArn": "string",
            "type": "NETWORK_REACHABILITY|PACKAGE_VULNERABILITY",
            "description": "string",
            "title": "string",
            "remediation": {
                "recommendation": {
                    "text": "string",
                    "url": "string"
                }
            },
            "severity": "INFORMATIONAL|LOW|MEDIUM|HIGH|CRITICAL|UNTRIAGED",
            "firstObservedAt": "timestamp",
            "updatedAt": "timestamp",
            "inspectorScore": "double",
            "inspectorScoreDetails": {
                "adjustedCvss": {
                    "scoreSource": "string",
                    "cvssSource": "string",
                    "version": "string",
                    "score": "double",
                    "scoringVector": "string",
                    "adjustments": []
                }
            },
            "packageVulnerabilityDetails": {
                "vulnerabilityId": "string",
                "vulnerablePackages": [
                    {
                        "name": "string",
                        "version": "string",
                        "sourceLayerHash": "string",
                        "epoch": "integer",
                        "release": "string",
                        "arch": "string",
                        "packageManager": "string",
                        "filePath": "string",
                        "fixedInVersion": "string",
                        "remediation": "string"
                    }
                ],
                "source": "string",
                "cvss": [],
                "relatedVulnerabilities": ["string"],
                "sourceUrl": "string",
                "vendorSeverity": "string",
                "vendorCreatedAt": "timestamp",
                "vendorUpdatedAt": "timestamp",
                "referenceUrls": ["string"]
            },
            "fixAvailable": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.2 `list-image-scan-finding-aggregations`

Lists aggregated image scan findings grouped by a specified category. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-image-scan-finding-aggregations \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | None | Filter for aggregation. Shorthand: `name=string,values=string,string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "requestId": "string",
    "aggregationType": "string",
    "responses": [
        {
            "accountAggregation": {
                "accountId": "string",
                "severityCounts": {
                    "all": "integer",
                    "critical": "integer",
                    "high": "integer",
                    "medium": "integer"
                }
            },
            "imageAggregation": {
                "imageBuildVersionArn": "string",
                "severityCounts": {}
            },
            "imagePipelineAggregation": {
                "imagePipelineArn": "string",
                "severityCounts": {}
            },
            "vulnerabilityIdAggregation": {
                "vulnerabilityId": "string",
                "severityCounts": {}
            }
        }
    ],
    "nextToken": "string"
}
```
