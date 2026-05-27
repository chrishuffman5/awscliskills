# Assets (VOD)

### 7.1 `create-asset`

Creates a VOD asset by ingesting content from S3. Egress endpoints are automatically created based on packaging configurations in the packaging group.

**Synopsis:**
```bash
aws mediapackage-vod create-asset \
    --id <value> \
    --packaging-group-id <value> \
    --source-arn <value> \
    --source-role-arn <value> \
    [--resource-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Unique identifier for the asset |
| `--packaging-group-id` | **Yes** | string | -- | ID of the packaging group for this asset |
| `--source-arn` | **Yes** | string | -- | ARN of the source object in S3 |
| `--source-role-arn` | **Yes** | string | -- | IAM role ARN for S3 access |
| `--resource-id` | No | string | None | Resource ID for SPEKE key requests |
| `--tags` | No | map | None | Key-value tag pairs |

**Output Schema:**
```json
{
    "Arn": "string",
    "CreatedAt": "string",
    "EgressEndpoints": [
        {
            "PackagingConfigurationId": "string",
            "Status": "string",
            "Url": "string"
        }
    ],
    "Id": "string",
    "PackagingGroupId": "string",
    "ResourceId": "string",
    "SourceArn": "string",
    "SourceRoleArn": "string",
    "Tags": {"string": "string"}
}
```

---

### 7.2 `describe-asset`

Describes a VOD asset including its egress endpoints.

**Synopsis:**
```bash
aws mediapackage-vod describe-asset \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the asset |

**Output Schema:**
```json
{
    "Arn": "string",
    "CreatedAt": "string",
    "EgressEndpoints": [
        {
            "PackagingConfigurationId": "string",
            "Status": "string",
            "Url": "string"
        }
    ],
    "Id": "string",
    "PackagingGroupId": "string",
    "ResourceId": "string",
    "SourceArn": "string",
    "SourceRoleArn": "string",
    "Tags": {"string": "string"}
}
```

---

### 7.3 `list-assets`

Lists all VOD assets, optionally filtered by packaging group. **Paginated operation.**

**Synopsis:**
```bash
aws mediapackage-vod list-assets \
    [--max-results <value>] \
    [--next-token <value>] \
    [--packaging-group-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Maximum number of results per page |
| `--next-token` | No | string | None | Pagination token |
| `--packaging-group-id` | No | string | None | Filter by packaging group ID |

**Output Schema:**
```json
{
    "Assets": [
        {
            "Arn": "string",
            "CreatedAt": "string",
            "Id": "string",
            "PackagingGroupId": "string",
            "ResourceId": "string",
            "SourceArn": "string",
            "SourceRoleArn": "string",
            "Tags": {"string": "string"}
        }
    ],
    "NextToken": "string"
}
```

---

### 7.4 `delete-asset`

Deletes a VOD asset.

**Synopsis:**
```bash
aws mediapackage-vod delete-asset \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the asset to delete |

**Output:** None
