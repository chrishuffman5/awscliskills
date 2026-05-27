# Findings

### 2.1 `list-findings`

Lists findings for your environment. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-findings \
    [--filter-criteria <value>] \
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
| `--filter-criteria` | No | structure | None | Filter criteria (JSON). See Filter Criteria below |
| `--sort-criteria` | No | structure | None | Sort field and order. Shorthand: `field=SEVERITY,sortOrder=ASC\|DESC` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Sort Fields:** `AWS_ACCOUNT_ID`, `FINDING_TYPE`, `SEVERITY`, `FIRST_OBSERVED_AT`, `LAST_OBSERVED_AT`, `FINDING_STATUS`, `RESOURCE_TYPE`, `ECR_IMAGE_PUSHED_AT`, `ECR_IMAGE_REPOSITORY_NAME`, `ECR_IMAGE_REGISTRY`, `NETWORK_PROTOCOL`, `COMPONENT_TYPE`, `VULNERABILITY_ID`, `VULNERABILITY_SOURCE`, `INSPECTOR_SCORE`, `VENDOR_SEVERITY`, `EPSS_SCORE`

**Filter Criteria Structure:**

String filters use `comparison` (`EQUALS`, `PREFIX`, `NOT_EQUALS`) and `value`:
- `findingArn`, `awsAccountId`, `findingType`, `severity`, `findingStatus`, `title`, `resourceType`, `resourceId`
- `ec2InstanceImageId`, `ec2InstanceVpcId`, `ec2InstanceSubnetId`
- `ecrImageArchitecture`, `ecrImageRegistry`, `ecrImageRepositoryName`, `ecrImageTags`, `ecrImageHash`
- `networkProtocol`, `componentId`, `componentType`, `vulnerabilityId`, `vulnerabilitySource`, `vendorSeverity`
- `relatedVulnerabilities`, `fixAvailable` (`YES`, `NO`, `PARTIAL`), `exploitAvailable` (`YES`, `NO`)
- `lambdaFunctionName`, `lambdaFunctionLayers`, `lambdaFunctionRuntime`, `lambdaFunctionExecutionRoleArn`
- `codeVulnerabilityDetectorName`, `codeVulnerabilityDetectorTags`, `codeVulnerabilityFilePath`
- `codeRepositoryProjectName`, `codeRepositoryProviderType`

Date range filters use `startInclusive` and `endInclusive`:
- `firstObservedAt`, `lastObservedAt`, `updatedAt`, `ecrImagePushedAt`, `ecrImageLastInUseAt`, `lambdaFunctionLastModifiedAt`

Number filters use `upperInclusive` and `lowerInclusive`:
- `inspectorScore`, `ecrImageInUseCount`, `epssScore`

Special filters:
- `resourceTags`: map filter with `comparison`, `key`, `value`
- `portRange`: `beginInclusive`, `endInclusive` (0-65535)
- `vulnerablePackages`: complex package filter

**Output Schema:**
```json
{
    "findings": [
        {
            "findingArn": "string",
            "awsAccountId": "string",
            "type": "NETWORK_REACHABILITY|PACKAGE_VULNERABILITY|CODE_VULNERABILITY",
            "description": "string",
            "title": "string",
            "severity": "INFORMATIONAL|LOW|MEDIUM|HIGH|CRITICAL|UNTRIAGED",
            "status": "ACTIVE|SUPPRESSED|CLOSED",
            "firstObservedAt": "timestamp",
            "lastObservedAt": "timestamp",
            "updatedAt": "timestamp",
            "inspectorScore": "double",
            "inspectorScoreDetails": {
                "adjustedCvss": {
                    "scoreSource": "string",
                    "cvssSource": "string",
                    "version": "string",
                    "score": "double",
                    "scoringVector": "string",
                    "adjustments": [
                        {
                            "metric": "string",
                            "reason": "string"
                        }
                    ]
                }
            },
            "remediation": {
                "recommendation": {
                    "text": "string",
                    "Url": "string"
                }
            },
            "resources": [
                {
                    "type": "AWS_EC2_INSTANCE|AWS_ECR_CONTAINER_IMAGE|AWS_ECR_REPOSITORY|AWS_LAMBDA_FUNCTION|CODE_REPOSITORY",
                    "id": "string",
                    "partition": "string",
                    "region": "string",
                    "tags": {"key": "value"},
                    "details": {
                        "awsEc2Instance": {
                            "type": "string",
                            "imageId": "string",
                            "ipV4Addresses": ["string"],
                            "ipV6Addresses": ["string"],
                            "keyName": "string",
                            "iamInstanceProfileArn": "string",
                            "vpcId": "string",
                            "subnetId": "string",
                            "launchedAt": "timestamp",
                            "platform": "string"
                        },
                        "awsEcrContainerImage": {
                            "repositoryName": "string",
                            "imageTags": ["string"],
                            "pushedAt": "timestamp",
                            "author": "string",
                            "architecture": "string",
                            "imageHash": "string",
                            "registry": "string",
                            "platform": "string"
                        },
                        "awsLambdaFunction": {
                            "functionName": "string",
                            "runtime": "string",
                            "codeSha256": "string",
                            "version": "string",
                            "executionRoleArn": "string",
                            "layers": ["string"],
                            "packageType": "IMAGE|ZIP",
                            "architectures": ["X86_64|ARM64"],
                            "lastModifiedAt": "timestamp"
                        },
                        "codeRepository": {
                            "projectName": "string",
                            "integrationArn": "string",
                            "providerType": "GITHUB|GITLAB_SELF_MANAGED"
                        }
                    }
                }
            ],
            "networkReachabilityDetails": {
                "openPortRange": {
                    "begin": "integer",
                    "end": "integer"
                },
                "protocol": "TCP|UDP",
                "networkPath": {
                    "steps": [
                        {
                            "componentId": "string",
                            "componentType": "string",
                            "componentArn": "string"
                        }
                    ]
                }
            },
            "packageVulnerabilityDetails": {
                "vulnerabilityId": "string",
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
                        "remediation": "string"
                    }
                ],
                "source": "string",
                "cvss": [
                    {
                        "baseScore": "double",
                        "scoringVector": "string",
                        "version": "string",
                        "source": "string"
                    }
                ],
                "relatedVulnerabilities": ["string"],
                "sourceUrl": "string",
                "vendorSeverity": "string",
                "vendorCreatedAt": "timestamp",
                "vendorUpdatedAt": "timestamp",
                "referenceUrls": ["string"]
            },
            "codeVulnerabilityDetails": {
                "filePath": {
                    "fileName": "string",
                    "filePath": "string",
                    "startLine": "integer",
                    "endLine": "integer"
                },
                "detectorTags": ["string"],
                "referenceUrls": ["string"],
                "ruleId": "string",
                "detectorId": "string",
                "detectorName": "string",
                "cwes": ["string"]
            },
            "fixAvailable": "YES|NO|PARTIAL",
            "exploitAvailable": "YES|NO",
            "exploitabilityDetails": {
                "lastKnownExploitAt": "timestamp"
            },
            "epss": {
                "score": "double"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 2.2 `list-finding-aggregations`

Lists finding aggregations grouped by a specified category. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-finding-aggregations \
    --aggregation-type <value> \
    [--aggregation-request <value>] \
    [--account-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aggregation-type` | **Yes** | string | -- | Aggregation type: `FINDING_TYPE`, `PACKAGE`, `TITLE`, `REPOSITORY`, `AMI`, `AWS_EC2_INSTANCE`, `AWS_ECR_CONTAINER`, `IMAGE_LAYER`, `ACCOUNT`, `AWS_LAMBDA_FUNCTION`, `LAMBDA_LAYER` |
| `--aggregation-request` | No | structure | None | Filter criteria for the aggregation |
| `--account-ids` | No | list | None | Account IDs with filter criteria |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "aggregationType": "string",
    "responses": [
        {
            "accountAggregation": {
                "accountId": "string",
                "severityCounts": {
                    "all": "long",
                    "critical": "long",
                    "high": "long",
                    "medium": "long"
                }
            },
            "titleAggregation": {
                "title": "string",
                "vulnerabilityId": "string",
                "accountId": "string",
                "severityCounts": {}
            },
            "packageAggregation": {
                "packageName": "string",
                "accountId": "string",
                "severityCounts": {}
            },
            "ec2InstanceAggregation": {
                "instanceId": "string",
                "ami": "string",
                "operatingSystem": "string",
                "instanceTags": {},
                "networkFindings": "long",
                "severityCounts": {}
            },
            "amiAggregation": {
                "ami": "string",
                "accountId": "string",
                "affectedInstances": "long",
                "severityCounts": {}
            },
            "findingTypeAggregation": {
                "accountId": "string",
                "severityCounts": {}
            },
            "imageLayerAggregation": {
                "layerHash": "string",
                "accountId": "string",
                "repository": "string",
                "resourceId": "string",
                "severityCounts": {}
            },
            "repositoryAggregation": {
                "repository": "string",
                "accountId": "string",
                "affectedImages": "long",
                "severityCounts": {}
            },
            "lambdaFunctionAggregation": {
                "functionName": "string",
                "resourceId": "string",
                "runtime": "string",
                "lambdaTags": {},
                "accountId": "string",
                "lastModifiedAt": "timestamp",
                "severityCounts": {}
            },
            "lambdaLayerAggregation": {
                "layerArn": "string",
                "functionName": "string",
                "resourceId": "string",
                "accountId": "string",
                "severityCounts": {}
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 2.3 `batch-get-finding-details`

Gets vulnerability details for one or more findings.

**Synopsis:**
```bash
aws inspector2 batch-get-finding-details \
    --finding-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-arns` | **Yes** | list(string) | -- | ARNs of findings to retrieve (max 25) |

**Output Schema:**
```json
{
    "findingDetails": [
        {
            "findingArn": "string",
            "cisaData": {
                "dateAdded": "timestamp",
                "dateDue": "timestamp",
                "action": "string"
            },
            "riskScore": "integer",
            "evidences": [
                {
                    "evidenceRule": "string",
                    "evidenceDetail": "string",
                    "severity": "string"
                }
            ],
            "ttps": [
                {
                    "id": "string",
                    "name": "string",
                    "url": "string"
                }
            ],
            "tools": ["string"],
            "referenceUrls": ["string"]
        }
    ],
    "errors": [
        {
            "findingArn": "string",
            "errorCode": "INTERNAL_ERROR|ACCESS_DENIED|FINDING_DETAILS_NOT_FOUND",
            "errorMessage": "string"
        }
    ]
}
```

---

### 2.4 `search-vulnerabilities`

Searches for vulnerability intelligence by CVE ID. **Paginated.**

**Synopsis:**
```bash
aws inspector2 search-vulnerabilities \
    --filter-criteria <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-criteria` | **Yes** | structure | -- | Filter by vulnerability IDs. Shorthand: `vulnerabilityIds=string,string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "vulnerabilities": [
        {
            "id": "string",
            "source": "NVD",
            "sourceUrl": "string",
            "description": "string",
            "cwes": ["string"],
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
            "vendorSeverity": "string",
            "vendorCreatedAt": "timestamp",
            "vendorUpdatedAt": "timestamp",
            "publishedAt": "timestamp",
            "exploitObserved": {
                "firstSeen": "timestamp",
                "lastSeen": "timestamp"
            },
            "detectionPlatforms": [
                {
                    "name": "string",
                    "version": "string"
                }
            ],
            "knownExploits": [
                {
                    "name": "string",
                    "url": "string"
                }
            ],
            "atigData": {
                "firstSeen": "timestamp",
                "lastSeen": "timestamp",
                "targets": ["string"],
                "ttps": ["string"]
            },
            "cisaData": {
                "dateAdded": "timestamp",
                "dateDue": "timestamp",
                "action": "string"
            },
            "epss": {
                "score": "double"
            }
        }
    ],
    "nextToken": "string"
}
```
