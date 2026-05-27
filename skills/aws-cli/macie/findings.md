# Findings

### 3.1 `get-findings`

Retrieves the details of one or more findings.

**Synopsis:**
```bash
aws macie2 get-findings \
    --finding-ids <value> \
    [--sort-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-ids` | **Yes** | list(string) | -- | Finding IDs to retrieve (max 50) |
| `--sort-criteria` | No | structure | None | Sort criteria |

**Sort Criteria Structure:**
```json
{
    "attributeName": "string",
    "orderBy": "ASC|DESC"
}
```

**Output Schema:**
```json
{
    "findings": [
        {
            "accountId": "string",
            "archived": "boolean",
            "category": "CLASSIFICATION|POLICY",
            "classificationDetails": {
                "detailedResultsLocation": "string",
                "jobArn": "string",
                "jobId": "string",
                "originType": "SENSITIVE_DATA_DISCOVERY_JOB|AUTOMATED_SENSITIVE_DATA_DISCOVERY",
                "result": {
                    "additionalOccurrences": "boolean",
                    "customDataIdentifiers": {
                        "detections": [
                            {
                                "arn": "string",
                                "count": "long",
                                "name": "string",
                                "occurrences": {}
                            }
                        ],
                        "totalCount": "long"
                    },
                    "mimeType": "string",
                    "sensitiveData": [
                        {
                            "category": "FINANCIAL_INFORMATION|PERSONAL_INFORMATION|CREDENTIALS|CUSTOM_IDENTIFIER",
                            "detections": [
                                {
                                    "count": "long",
                                    "occurrences": {},
                                    "type": "string"
                                }
                            ],
                            "totalCount": "long"
                        }
                    ],
                    "sizeClassified": "long",
                    "status": {
                        "code": "string",
                        "reason": "string"
                    }
                }
            },
            "count": "long",
            "createdAt": "timestamp",
            "description": "string",
            "id": "string",
            "partition": "string",
            "policyDetails": {
                "action": {
                    "actionType": "AWS_API_CALL",
                    "apiCallDetails": {
                        "api": "string",
                        "apiServiceName": "string",
                        "firstSeen": "timestamp",
                        "lastSeen": "timestamp"
                    }
                },
                "actor": {
                    "domainDetails": {"domainName": "string"},
                    "ipAddressDetails": {},
                    "userIdentity": {}
                }
            },
            "region": "string",
            "resourcesAffected": {
                "s3Bucket": {
                    "arn": "string",
                    "createdAt": "timestamp",
                    "defaultServerSideEncryption": {},
                    "name": "string",
                    "owner": {"displayName": "string", "id": "string"},
                    "publicAccess": {},
                    "tags": []
                },
                "s3Object": {
                    "bucketArn": "string",
                    "eTag": "string",
                    "extension": "string",
                    "key": "string",
                    "lastModified": "timestamp",
                    "path": "string",
                    "publicAccess": "boolean",
                    "serverSideEncryption": {},
                    "size": "long",
                    "storageClass": "string",
                    "tags": [],
                    "versionId": "string"
                }
            },
            "sample": "boolean",
            "schemaVersion": "string",
            "severity": {
                "description": "Low|Medium|High",
                "score": "long"
            },
            "title": "string",
            "type": "string",
            "updatedAt": "timestamp"
        }
    ]
}
```

---

### 3.2 `list-findings`

Retrieves a subset of information about findings. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-findings \
    [--finding-criteria <value>] \
    [--sort-criteria <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-criteria` | No | structure | None | Filter criteria for findings |
| `--sort-criteria` | No | structure | None | Sort criteria |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Finding Criteria Structure:**
```json
{
    "criterion": {
        "string": {
            "eq": ["string"],
            "neq": ["string"],
            "gt": "long",
            "gte": "long",
            "lt": "long",
            "lte": "long",
            "eqExactMatch": ["string"]
        }
    }
}
```

**Output Schema:**
```json
{
    "findingIds": ["string"],
    "nextToken": "string"
}
```

---

### 3.3 `get-finding-statistics`

Retrieves aggregated statistical data about findings.

**Synopsis:**
```bash
aws macie2 get-finding-statistics \
    --group-by <value> \
    [--finding-criteria <value>] \
    [--size <value>] \
    [--sort-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-by` | **Yes** | string | -- | Group by: `resourcesAffected.s3Bucket.name`, `type`, `classificationDetails.jobId`, `severity.description` |
| `--finding-criteria` | No | structure | None | Filter criteria |
| `--size` | No | integer | None | Max groups to return |
| `--sort-criteria` | No | structure | None | Sort criteria |

**Output Schema:**
```json
{
    "countsByGroup": [
        {
            "count": "long",
            "groupKey": "string"
        }
    ]
}
```

---

### 3.4 `create-sample-findings`

Creates sample findings for testing purposes.

**Synopsis:**
```bash
aws macie2 create-sample-findings \
    [--finding-types <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-types` | No | list(string) | None | Types of sample findings to generate |

**Output:** None (HTTP 200 on success)
