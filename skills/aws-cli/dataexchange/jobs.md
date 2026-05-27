# Jobs

## 3.1 `create-job`

Creates an import or export job.

**Synopsis:**
```bash
aws dataexchange create-job \
    --type <value> \
    --details <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Job type (see Job Types in index.md) |
| `--details` | **Yes** | structure | -- | Job-type-specific details |

**Import from S3 Details:**
```json
{
    "ImportAssetsFromS3": {
        "DataSetId": "string",
        "RevisionId": "string",
        "AssetSources": [
            {
                "Bucket": "my-bucket",
                "Key": "data/file.csv"
            }
        ]
    }
}
```

**Export to S3 Details:**
```json
{
    "ExportAssetsToS3": {
        "DataSetId": "string",
        "RevisionId": "string",
        "AssetDestinations": [
            {
                "AssetId": "string",
                "Bucket": "export-bucket",
                "Key": "exports/file.csv"
            }
        ],
        "Encryption": {
            "Type": "aws:kms|AES256",
            "KmsKeyArn": "string"
        }
    }
}
```

**Export Revisions to S3 Details:**
```json
{
    "ExportRevisionsToS3": {
        "DataSetId": "string",
        "RevisionDestinations": [
            {
                "RevisionId": "string",
                "Bucket": "export-bucket",
                "KeyPattern": "${Revision.CreatedAt}/${Asset.Name}"
            }
        ],
        "Encryption": {
            "Type": "AES256"
        }
    }
}
```

**Import from Signed URL Details:**
```json
{
    "ImportAssetFromSignedUrl": {
        "AssetName": "my-file.csv",
        "DataSetId": "string",
        "Md5Hash": "string",
        "RevisionId": "string"
    }
}
```

**Import Redshift Data Shares Details:**
```json
{
    "ImportAssetsFromRedshiftDataShares": {
        "DataSetId": "string",
        "RevisionId": "string",
        "AssetSources": [
            {
                "DataShareArn": "arn:aws:redshift:..."
            }
        ]
    }
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "CreatedAt": "timestamp",
    "Details": {
        "ExportAssetToSignedUrl": {},
        "ExportAssetsToS3": {},
        "ExportRevisionsToS3": {},
        "ImportAssetFromSignedUrl": {},
        "ImportAssetsFromS3": {},
        "ImportAssetsFromRedshiftDataShares": {},
        "ImportAssetFromApiGatewayApi": {},
        "CreateS3DataAccessFromS3Bucket": {},
        "ImportAssetsFromLakeFormationTagPolicy": {}
    },
    "Errors": [
        {
            "Code": "string",
            "Message": "string",
            "ResourceId": "string",
            "ResourceType": "REVISION|ASSET|DATA_SET",
            "LimitName": "string",
            "LimitValue": "number"
        }
    ],
    "Id": "string",
    "State": "WAITING|IN_PROGRESS|ERROR|COMPLETED|CANCELLED|TIMED_OUT",
    "Type": "string",
    "UpdatedAt": "timestamp"
}
```

---

## 3.2 `start-job`

Starts a job that was previously created. The job must be in `WAITING` state.

**Synopsis:**
```bash
aws dataexchange start-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | ID of the job to start |

**Output Schema:**

None (HTTP 202 on success).

---

## 3.3 `get-job`

Returns details and status of a job.

**Synopsis:**
```bash
aws dataexchange get-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |

**Output Schema:**
```json
{
    "Arn": "string",
    "CreatedAt": "timestamp",
    "Details": {},
    "Errors": [],
    "Id": "string",
    "State": "WAITING|IN_PROGRESS|ERROR|COMPLETED|CANCELLED|TIMED_OUT",
    "Type": "string",
    "UpdatedAt": "timestamp"
}
```

---

## 3.4 `list-jobs`

Lists jobs. **Paginated operation.**

**Synopsis:**
```bash
aws dataexchange list-jobs \
    [--data-set-id <value>] \
    [--revision-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | No | string | None | Filter by data set ID |
| `--revision-id` | No | string | None | Filter by revision ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Jobs": [
        {
            "Arn": "string",
            "CreatedAt": "timestamp",
            "Details": {},
            "Errors": [],
            "Id": "string",
            "State": "string",
            "Type": "string",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 3.5 `cancel-job`

Cancels a job in `WAITING` or `IN_PROGRESS` state.

**Synopsis:**
```bash
aws dataexchange cancel-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | ID of the job to cancel |

**Output Schema:**

None (HTTP 204 on success).
