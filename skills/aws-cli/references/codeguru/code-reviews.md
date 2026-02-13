# Code Reviews

### 2.1 `create-code-review`

Creates a code review to analyze code in a repository. Uses `aws codeguru-reviewer`.

**Synopsis:**
```bash
aws codeguru-reviewer create-code-review \
    --name <value> \
    --repository-association-arn <value> \
    --type <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the code review |
| `--repository-association-arn` | **Yes** | string | -- | ARN of the repository association |
| `--type` | **Yes** | structure | -- | Type of code review. JSON: `{"RepositoryAnalysis":{"RepositoryHead":{"BranchName":"string"}}}` or `{"RepositoryAnalysis":{"SourceCodeType":{"S3BucketRepository":{"Name":"string","Details":{"BucketName":"string","CodeArtifacts":{"SourceCodeArtifactsObjectKey":"string","BuildArtifactsObjectKey":"string"}}}}}}` |
| `--client-request-token` | No | string | None | Unique idempotency token (auto-generated if not specified) |

**Type Structure (RepositoryHead):**
```json
{
    "RepositoryAnalysis": {
        "RepositoryHead": {
            "BranchName": "string"
        }
    }
}
```

**Type Structure (S3BucketRepository):**
```json
{
    "RepositoryAnalysis": {
        "SourceCodeType": {
            "S3BucketRepository": {
                "Name": "string",
                "Details": {
                    "BucketName": "string",
                    "CodeArtifacts": {
                        "SourceCodeArtifactsObjectKey": "string",
                        "BuildArtifactsObjectKey": "string"
                    }
                }
            }
        }
    }
}
```

**Output Schema:**
```json
{
    "CodeReview": {
        "Name": "string",
        "CodeReviewArn": "string",
        "RepositoryName": "string",
        "Owner": "string",
        "ProviderType": "CodeCommit|Bitbucket|GitHubEnterpriseServer|S3Bucket",
        "State": "Completed|Pending|Failed|Deleting",
        "StateReason": "string",
        "CreatedTimeStamp": "timestamp",
        "LastUpdatedTimeStamp": "timestamp",
        "Type": "PullRequest|RepositoryAnalysis",
        "PullRequestId": "string",
        "SourceCodeType": {
            "CommitDiff": {
                "SourceCommit": "string",
                "DestinationCommit": "string",
                "MergeBaseCommit": "string"
            },
            "RepositoryHead": {
                "BranchName": "string"
            },
            "BranchDiff": {
                "SourceBranchName": "string",
                "DestinationBranchName": "string"
            },
            "S3BucketRepository": {
                "Name": "string",
                "Details": {
                    "BucketName": "string",
                    "CodeArtifacts": {
                        "SourceCodeArtifactsObjectKey": "string",
                        "BuildArtifactsObjectKey": "string"
                    }
                }
            },
            "RequestMetadata": {
                "RequestId": "string",
                "Requester": "string",
                "EventInfo": {
                    "Name": "string",
                    "State": "string"
                },
                "VendorName": "GitHub|GitLab|NativeS3"
            }
        },
        "AssociationArn": "string",
        "Metrics": {
            "MeteredLinesOfCodeCount": "long",
            "SuppressedLinesOfCodeCount": "long",
            "FindingsCount": "long"
        },
        "AnalysisTypes": ["Security|CodeQuality"],
        "ConfigFileState": "Present|Absent|PresentWithErrors"
    }
}
```

---

### 2.2 `describe-code-review`

Returns the metadata associated with a code review.

**Synopsis:**
```bash
aws codeguru-reviewer describe-code-review \
    --code-review-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-review-arn` | **Yes** | string | -- | ARN of the code review to describe |

**Output Schema:**
```json
{
    "CodeReview": {
        "Name": "string",
        "CodeReviewArn": "string",
        "RepositoryName": "string",
        "Owner": "string",
        "ProviderType": "CodeCommit|Bitbucket|GitHubEnterpriseServer|S3Bucket",
        "State": "Completed|Pending|Failed|Deleting",
        "StateReason": "string",
        "CreatedTimeStamp": "timestamp",
        "LastUpdatedTimeStamp": "timestamp",
        "Type": "PullRequest|RepositoryAnalysis",
        "PullRequestId": "string",
        "SourceCodeType": {
            "CommitDiff": {
                "SourceCommit": "string",
                "DestinationCommit": "string",
                "MergeBaseCommit": "string"
            },
            "RepositoryHead": {
                "BranchName": "string"
            }
        },
        "AssociationArn": "string",
        "Metrics": {
            "MeteredLinesOfCodeCount": "long",
            "SuppressedLinesOfCodeCount": "long",
            "FindingsCount": "long"
        },
        "AnalysisTypes": ["Security|CodeQuality"],
        "ConfigFileState": "Present|Absent|PresentWithErrors"
    }
}
```

---

### 2.3 `list-code-reviews`

Lists all code reviews that the customer has created in the past 90 days. **Paginated operation.**

**Synopsis:**
```bash
aws codeguru-reviewer list-code-reviews \
    --type <value> \
    [--provider-types <value>] \
    [--states <value>] \
    [--repository-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Type of code reviews: `PullRequest` or `RepositoryAnalysis` |
| `--provider-types` | No | list(string) | None | Filter by provider: `CodeCommit`, `Bitbucket`, `GitHubEnterpriseServer`, `S3Bucket` |
| `--states` | No | list(string) | None | Filter by state: `Completed`, `Pending`, `Failed`, `Deleting` |
| `--repository-names` | No | list(string) | None | Filter by repository name |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CodeReviewSummaries": [
        {
            "Name": "string",
            "CodeReviewArn": "string",
            "RepositoryName": "string",
            "Owner": "string",
            "ProviderType": "CodeCommit|Bitbucket|GitHubEnterpriseServer|S3Bucket",
            "State": "Completed|Pending|Failed|Deleting",
            "CreatedTimeStamp": "timestamp",
            "LastUpdatedTimeStamp": "timestamp",
            "Type": "PullRequest|RepositoryAnalysis",
            "PullRequestId": "string",
            "MetricsSummary": {
                "MeteredLinesOfCodeCount": "long",
                "SuppressedLinesOfCodeCount": "long",
                "FindingsCount": "long"
            },
            "SourceCodeType": {
                "CommitDiff": {},
                "RepositoryHead": {},
                "BranchDiff": {},
                "S3BucketRepository": {},
                "RequestMetadata": {}
            }
        }
    ],
    "NextToken": "string"
}
```
