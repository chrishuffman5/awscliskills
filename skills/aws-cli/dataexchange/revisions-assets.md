# Revisions & Assets

## 2.1 `create-revision`

Creates a new revision in a data set.

**Synopsis:**
```bash
aws dataexchange create-revision \
    --data-set-id <value> \
    [--comment <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--comment` | No | string | None | Comment about the revision (max 16,384 chars) |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "Arn": "string",
    "Comment": "string",
    "CreatedAt": "timestamp",
    "DataSetId": "string",
    "Finalized": "boolean",
    "Id": "string",
    "SourceId": "string",
    "Tags": { "string": "string" },
    "UpdatedAt": "timestamp",
    "RevocationComment": "string",
    "Revoked": "boolean",
    "RevokedAt": "timestamp"
}
```

---

## 2.2 `get-revision`

Returns details for a revision.

**Synopsis:**
```bash
aws dataexchange get-revision \
    --data-set-id <value> \
    --revision-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--revision-id` | **Yes** | string | -- | Revision ID |

**Output Schema:**
```json
{
    "Arn": "string",
    "Comment": "string",
    "CreatedAt": "timestamp",
    "DataSetId": "string",
    "Finalized": "boolean",
    "Id": "string",
    "SourceId": "string",
    "Tags": { "string": "string" },
    "UpdatedAt": "timestamp",
    "RevocationComment": "string",
    "Revoked": "boolean",
    "RevokedAt": "timestamp"
}
```

---

## 2.3 `list-data-set-revisions`

Lists revisions for a data set. **Paginated operation.**

**Synopsis:**
```bash
aws dataexchange list-data-set-revisions \
    --data-set-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Revisions": [
        {
            "Arn": "string",
            "Comment": "string",
            "CreatedAt": "timestamp",
            "DataSetId": "string",
            "Finalized": "boolean",
            "Id": "string",
            "SourceId": "string",
            "UpdatedAt": "timestamp",
            "RevocationComment": "string",
            "Revoked": "boolean",
            "RevokedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 2.4 `update-revision`

Updates a revision (e.g., to finalize it for publishing).

**Synopsis:**
```bash
aws dataexchange update-revision \
    --data-set-id <value> \
    --revision-id <value> \
    [--comment <value>] \
    [--finalized | --no-finalized] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--revision-id` | **Yes** | string | -- | Revision ID |
| `--comment` | No | string | None | Updated comment |
| `--finalized` / `--no-finalized` | No | boolean | None | Finalize the revision (makes it read-only) |

**Output Schema:**
```json
{
    "Arn": "string",
    "Comment": "string",
    "CreatedAt": "timestamp",
    "DataSetId": "string",
    "Finalized": "boolean",
    "Id": "string",
    "SourceId": "string",
    "Tags": { "string": "string" },
    "UpdatedAt": "timestamp",
    "RevocationComment": "string",
    "Revoked": "boolean",
    "RevokedAt": "timestamp"
}
```

---

## 2.5 `delete-revision`

Deletes a revision. Only non-finalized revisions can be deleted.

**Synopsis:**
```bash
aws dataexchange delete-revision \
    --data-set-id <value> \
    --revision-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--revision-id` | **Yes** | string | -- | Revision ID to delete |

**Output Schema:**

None (HTTP 204 on success).

---

## 2.6 `revoke-revision`

Revokes subscriber access to a published revision.

**Synopsis:**
```bash
aws dataexchange revoke-revision \
    --data-set-id <value> \
    --revision-id <value> \
    --revocation-comment <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--revision-id` | **Yes** | string | -- | Revision ID to revoke |
| `--revocation-comment` | **Yes** | string | -- | Reason for revocation (10-512 chars) |

**Output Schema:**
```json
{
    "Arn": "string",
    "Comment": "string",
    "CreatedAt": "timestamp",
    "DataSetId": "string",
    "Finalized": "boolean",
    "Id": "string",
    "SourceId": "string",
    "UpdatedAt": "timestamp",
    "RevocationComment": "string",
    "Revoked": true,
    "RevokedAt": "timestamp"
}
```

---

## 2.7 `get-asset`

Returns details for an asset.

**Synopsis:**
```bash
aws dataexchange get-asset \
    --data-set-id <value> \
    --revision-id <value> \
    --asset-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--revision-id` | **Yes** | string | -- | Revision ID |
| `--asset-id` | **Yes** | string | -- | Asset ID |

**Output Schema:**
```json
{
    "Arn": "string",
    "AssetDetails": {
        "S3SnapshotAsset": { "Size": "double" },
        "RedshiftDataShareAsset": {
            "Arn": "string"
        },
        "ApiGatewayApiAsset": {
            "ApiDescription": "string",
            "ApiEndpoint": "string",
            "ApiId": "string",
            "ApiKey": "string",
            "ApiName": "string",
            "ApiSpecificationDownloadUrl": "string",
            "ApiSpecificationDownloadUrlExpiresAt": "timestamp",
            "ProtocolType": "REST",
            "Stage": "string"
        },
        "S3DataAccessAsset": {
            "Bucket": "string",
            "KeyPrefixes": ["string"],
            "Keys": ["string"],
            "S3AccessPointAlias": "string",
            "S3AccessPointArn": "string",
            "KmsKeysToGrant": [{ "KmsKeyArn": "string" }]
        },
        "LakeFormationDataPermissionAsset": {
            "LakeFormationDataPermissionDetails": {},
            "LakeFormationDataPermissionType": "LFTagPolicy",
            "Permissions": ["string"],
            "RoleArn": "string"
        }
    },
    "AssetType": "string",
    "CreatedAt": "timestamp",
    "DataSetId": "string",
    "Id": "string",
    "Name": "string",
    "RevisionId": "string",
    "SourceId": "string",
    "UpdatedAt": "timestamp"
}
```

---

## 2.8 `list-revision-assets`

Lists assets in a revision. **Paginated operation.**

**Synopsis:**
```bash
aws dataexchange list-revision-assets \
    --data-set-id <value> \
    --revision-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--revision-id` | **Yes** | string | -- | Revision ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Assets": [
        {
            "Arn": "string",
            "AssetDetails": {},
            "AssetType": "string",
            "CreatedAt": "timestamp",
            "DataSetId": "string",
            "Id": "string",
            "Name": "string",
            "RevisionId": "string",
            "SourceId": "string",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 2.9 `update-asset`

Updates an asset's name.

**Synopsis:**
```bash
aws dataexchange update-asset \
    --data-set-id <value> \
    --revision-id <value> \
    --asset-id <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--revision-id` | **Yes** | string | -- | Revision ID |
| `--asset-id` | **Yes** | string | -- | Asset ID |
| `--name` | **Yes** | string | -- | New asset name |

**Output Schema:**
```json
{
    "Arn": "string",
    "AssetDetails": {},
    "AssetType": "string",
    "CreatedAt": "timestamp",
    "DataSetId": "string",
    "Id": "string",
    "Name": "string",
    "RevisionId": "string",
    "SourceId": "string",
    "UpdatedAt": "timestamp"
}
```

---

## 2.10 `delete-asset`

Deletes an asset from a revision.

**Synopsis:**
```bash
aws dataexchange delete-asset \
    --data-set-id <value> \
    --revision-id <value> \
    --asset-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--revision-id` | **Yes** | string | -- | Revision ID |
| `--asset-id` | **Yes** | string | -- | Asset ID to delete |

**Output Schema:**

None (HTTP 204 on success).

---

## 2.11 `send-api-asset`

Sends a request to the API asset endpoint. Used for API_GATEWAY_API type assets.

**Synopsis:**
```bash
aws dataexchange send-api-asset \
    --data-set-id <value> \
    --revision-id <value> \
    --asset-id <value> \
    [--body <value>] \
    [--method <value>] \
    [--path <value>] \
    [--query-string-parameters <value>] \
    [--request-headers <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-set-id` | **Yes** | string | -- | Data set ID |
| `--revision-id` | **Yes** | string | -- | Revision ID |
| `--asset-id` | **Yes** | string | -- | Asset ID |
| `--body` | No | string | None | Request body content |
| `--method` | No | string | None | HTTP method (GET, POST, etc.) |
| `--path` | No | string | None | URI path for the request |
| `--query-string-parameters` | No | map | None | Query string key-value pairs |
| `--request-headers` | No | map | None | Request header key-value pairs |

**Output Schema:**
```json
{
    "Body": "string",
    "ResponseHeaders": { "string": "string" }
}
```
