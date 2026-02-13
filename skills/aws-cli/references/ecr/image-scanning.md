# Image Scanning

### 3.1 `describe-image-scan-findings`

Returns the scan findings for a specified image. **Paginated operation.**

**Synopsis:**
```bash
aws ecr describe-image-scan-findings \
    --repository-name <value> \
    --image-id <value> \
    [--registry-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--image-id` | **Yes** | structure | -- | `imageDigest=string,imageTag=string` |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "registryId": "string",
    "repositoryName": "string",
    "imageId": {
        "imageDigest": "string",
        "imageTag": "string"
    },
    "imageScanStatus": {
        "status": "IN_PROGRESS|COMPLETE|FAILED|UNSUPPORTED_IMAGE|ACTIVE|PENDING|SCAN_ELIGIBILITY_EXPIRED|FINDINGS_UNAVAILABLE|LIMIT_EXCEEDED|IMAGE_ARCHIVED",
        "description": "string"
    },
    "imageScanFindings": {
        "imageScanCompletedAt": "timestamp",
        "vulnerabilitySourceUpdatedAt": "timestamp",
        "findingSeverityCounts": {
            "INFORMATIONAL": "integer",
            "LOW": "integer",
            "MEDIUM": "integer",
            "HIGH": "integer",
            "CRITICAL": "integer",
            "UNDEFINED": "integer"
        },
        "findings": [
            {
                "name": "string",
                "description": "string",
                "uri": "string",
                "severity": "INFORMATIONAL|LOW|MEDIUM|HIGH|CRITICAL|UNDEFINED",
                "attributes": [
                    {
                        "key": "string",
                        "value": "string"
                    }
                ]
            }
        ],
        "enhancedFindings": [
            {
                "awsAccountId": "string",
                "description": "string",
                "findingArn": "string",
                "firstObservedAt": "timestamp",
                "lastObservedAt": "timestamp",
                "packageVulnerabilityDetails": {
                    "vulnerabilityId": "string",
                    "vendorSeverity": "string",
                    "source": "string",
                    "sourceUrl": "string",
                    "cvss": [
                        {
                            "baseScore": "double",
                            "scoringVector": "string",
                            "version": "string",
                            "source": "string"
                        }
                    ],
                    "referenceUrls": ["string"],
                    "relatedVulnerabilities": ["string"],
                    "vendorCreatedAt": "timestamp",
                    "vendorUpdatedAt": "timestamp",
                    "vulnerablePackages": [
                        {
                            "name": "string",
                            "version": "string",
                            "epoch": "integer",
                            "release": "string",
                            "arch": "string",
                            "packageManager": "string",
                            "filePath": "string",
                            "fixedInVersion": "string",
                            "sourceLayerHash": "string"
                        }
                    ]
                },
                "remediation": {
                    "recommendation": {
                        "text": "string",
                        "url": "string"
                    }
                },
                "resources": [
                    {
                        "type": "string",
                        "id": "string",
                        "tags": {"string": "string"},
                        "details": {
                            "awsEcrContainerImage": {
                                "imageHash": "string",
                                "imageTags": ["string"],
                                "architecture": "string",
                                "author": "string",
                                "platform": "string",
                                "pushedAt": "timestamp",
                                "lastInUseAt": "timestamp",
                                "inUseCount": "long",
                                "registry": "string",
                                "repositoryName": "string"
                            }
                        }
                    }
                ],
                "severity": "INFORMATIONAL|LOW|MEDIUM|HIGH|CRITICAL|UNDEFINED",
                "status": "string",
                "title": "string",
                "type": "string",
                "score": "double",
                "scoreDetails": {
                    "cvss": {
                        "score": "double",
                        "version": "string",
                        "scoreSource": "string",
                        "scoringVector": "string",
                        "adjustments": [
                            {
                                "metric": "string",
                                "reason": "string"
                            }
                        ]
                    }
                },
                "updatedAt": "timestamp",
                "fixAvailable": "YES|NO|PARTIAL",
                "exploitAvailable": "string"
            }
        ]
    },
    "nextToken": "string"
}
```

---

### 3.2 `start-image-scan`

Starts an image vulnerability scan. Limited to one basic scan per image per 24 hours, up to 100,000 scans per 24 hours.

**Synopsis:**
```bash
aws ecr start-image-scan \
    --repository-name <value> \
    --image-id <value> \
    [--registry-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--image-id` | **Yes** | structure | -- | `imageDigest=string,imageTag=string` |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |

**Output Schema:**
```json
{
    "registryId": "string",
    "repositoryName": "string",
    "imageId": {
        "imageDigest": "string",
        "imageTag": "string"
    },
    "imageScanStatus": {
        "status": "IN_PROGRESS|COMPLETE|FAILED|UNSUPPORTED_IMAGE|ACTIVE|PENDING|SCAN_ELIGIBILITY_EXPIRED|FINDINGS_UNAVAILABLE|LIMIT_EXCEEDED|IMAGE_ARCHIVED",
        "description": "string"
    }
}
```

---

### 3.3 `put-image-scanning-configuration`

Updates the image scanning configuration for a repository.

> **Deprecated:** Use `put-registry-scanning-configuration` for registry-level configuration instead.

**Synopsis:**
```bash
aws ecr put-image-scanning-configuration \
    --repository-name <value> \
    --image-scanning-configuration <value> \
    [--registry-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--image-scanning-configuration` | **Yes** | structure | -- | Shorthand: `scanOnPush=true\|false` |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |

**Output Schema:**
```json
{
    "registryId": "string",
    "repositoryName": "string",
    "imageScanningConfiguration": {
        "scanOnPush": true|false
    }
}
```

---

