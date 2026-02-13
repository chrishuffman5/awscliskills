# Repositories

### 1.1 `associate-repository`

Associates a repository with CodeGuru Reviewer for automated code reviews.

**Synopsis:**
```bash
aws codeguru-reviewer associate-repository \
    --repository <value> \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--kms-key-details <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository` | **Yes** | structure | -- | Repository to associate. Shorthand: `CodeCommit={Name=string}`, `Bitbucket={Name=string,ConnectionArn=string,Owner=string}`, `GitHubEnterpriseServer={Name=string,ConnectionArn=string,Owner=string}`, `S3Bucket={Name=string,BucketName=string}` |
| `--client-request-token` | No | string | None | Unique idempotency token (auto-generated if not specified) |
| `--tags` | No | map | None | Tags to associate. Shorthand: `KeyName1=string,KeyName2=string` |
| `--kms-key-details` | No | structure | None | KMS key for encrypting code reviews. Shorthand: `KMSKeyId=string,EncryptionOption=AWS_OWNED_CMK\|CUSTOMER_MANAGED_CMK` |

**Output Schema:**
```json
{
    "RepositoryAssociation": {
        "AssociationId": "string",
        "AssociationArn": "string",
        "ConnectionArn": "string",
        "Name": "string",
        "Owner": "string",
        "ProviderType": "CodeCommit|Bitbucket|GitHubEnterpriseServer|S3Bucket",
        "State": "Associated|Associating|Failed|Disassociating|Disassociated",
        "StateReason": "string",
        "LastUpdatedTimeStamp": "timestamp",
        "CreatedTimeStamp": "timestamp",
        "KMSKeyDetails": {
            "KMSKeyId": "string",
            "EncryptionOption": "AWS_OWNED_CMK|CUSTOMER_MANAGED_CMK"
        },
        "S3RepositoryDetails": {
            "BucketName": "string",
            "CodeArtifacts": {
                "SourceCodeArtifactsObjectKey": "string",
                "BuildArtifactsObjectKey": "string"
            }
        }
    },
    "Tags": {
        "string": "string"
    }
}
```

---

### 1.2 `disassociate-repository`

Removes a repository association from CodeGuru Reviewer.

**Synopsis:**
```bash
aws codeguru-reviewer disassociate-repository \
    --association-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-arn` | **Yes** | string | -- | ARN of the repository association to disassociate |

**Output Schema:**
```json
{
    "RepositoryAssociation": {
        "AssociationId": "string",
        "AssociationArn": "string",
        "ConnectionArn": "string",
        "Name": "string",
        "Owner": "string",
        "ProviderType": "CodeCommit|Bitbucket|GitHubEnterpriseServer|S3Bucket",
        "State": "Disassociating|Disassociated",
        "StateReason": "string",
        "LastUpdatedTimeStamp": "timestamp",
        "CreatedTimeStamp": "timestamp"
    },
    "Tags": {
        "string": "string"
    }
}
```

---

### 1.3 `describe-repository-association`

Returns a repository association object that contains detailed information about the association.

**Synopsis:**
```bash
aws codeguru-reviewer describe-repository-association \
    --association-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-arn` | **Yes** | string | -- | ARN of the repository association to describe |

**Output Schema:**
```json
{
    "RepositoryAssociation": {
        "AssociationId": "string",
        "AssociationArn": "string",
        "ConnectionArn": "string",
        "Name": "string",
        "Owner": "string",
        "ProviderType": "CodeCommit|Bitbucket|GitHubEnterpriseServer|S3Bucket",
        "State": "Associated|Associating|Failed|Disassociating|Disassociated",
        "StateReason": "string",
        "LastUpdatedTimeStamp": "timestamp",
        "CreatedTimeStamp": "timestamp",
        "KMSKeyDetails": {
            "KMSKeyId": "string",
            "EncryptionOption": "AWS_OWNED_CMK|CUSTOMER_MANAGED_CMK"
        },
        "S3RepositoryDetails": {
            "BucketName": "string",
            "CodeArtifacts": {
                "SourceCodeArtifactsObjectKey": "string",
                "BuildArtifactsObjectKey": "string"
            }
        }
    },
    "Tags": {
        "string": "string"
    }
}
```

---

### 1.4 `list-repository-associations`

Returns a list of repository associations. **Paginated operation.**

**Synopsis:**
```bash
aws codeguru-reviewer list-repository-associations \
    [--provider-types <value>] \
    [--states <value>] \
    [--names <value>] \
    [--owners <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provider-types` | No | list(string) | None | Filter by provider type: `CodeCommit`, `Bitbucket`, `GitHubEnterpriseServer`, `S3Bucket` |
| `--states` | No | list(string) | None | Filter by state: `Associated`, `Associating`, `Failed`, `Disassociating`, `Disassociated` |
| `--names` | No | list(string) | None | Filter by repository name |
| `--owners` | No | list(string) | None | Filter by repository owner |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RepositoryAssociationSummaries": [
        {
            "AssociationArn": "string",
            "ConnectionArn": "string",
            "LastUpdatedTimeStamp": "timestamp",
            "AssociationId": "string",
            "Name": "string",
            "Owner": "string",
            "ProviderType": "CodeCommit|Bitbucket|GitHubEnterpriseServer|S3Bucket",
            "State": "Associated|Associating|Failed|Disassociating|Disassociated"
        }
    ],
    "NextToken": "string"
}
```
