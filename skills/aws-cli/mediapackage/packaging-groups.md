# Packaging Groups (VOD)

### 5.1 `create-packaging-group`

Creates a packaging group for VOD content distribution.

**Synopsis:**
```bash
aws mediapackage-vod create-packaging-group \
    --id <value> \
    [--authorization <value>] \
    [--egress-access-logs <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Unique ID for the packaging group |
| `--authorization` | No | structure | None | CDN authorization credentials |
| `--egress-access-logs` | No | structure | None | Egress access logging config |
| `--tags` | No | map | None | Key-value tag pairs |

**Authorization:**
```json
{
    "CdnIdentifierSecret": "arn:aws:secretsmanager:us-east-1:123456789012:secret:cdn-secret",
    "SecretsRoleArn": "arn:aws:iam::123456789012:role/MediaPackageSecretsRole"
}
```

**EgressAccessLogs:**
```json
{
    "LogGroupName": "/aws/mediapackage-vod/my-group"
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "CreatedAt": "string",
    "DomainName": "string",
    "Authorization": {
        "CdnIdentifierSecret": "string",
        "SecretsRoleArn": "string"
    },
    "EgressAccessLogs": {
        "LogGroupName": "string"
    },
    "Tags": {"string": "string"}
}
```

---

### 5.2 `describe-packaging-group`

Describes a packaging group.

**Synopsis:**
```bash
aws mediapackage-vod describe-packaging-group \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the packaging group |

**Output Schema:**
```json
{
    "ApproximateAssetCount": "integer",
    "Arn": "string",
    "Authorization": {
        "CdnIdentifierSecret": "string",
        "SecretsRoleArn": "string"
    },
    "CreatedAt": "string",
    "DomainName": "string",
    "EgressAccessLogs": {
        "LogGroupName": "string"
    },
    "Id": "string",
    "Tags": {"string": "string"}
}
```

---

### 5.3 `list-packaging-groups`

Lists all packaging groups. **Paginated operation.**

**Synopsis:**
```bash
aws mediapackage-vod list-packaging-groups \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Maximum number of results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "PackagingGroups": [
        {
            "ApproximateAssetCount": "integer",
            "Arn": "string",
            "Authorization": {
                "CdnIdentifierSecret": "string",
                "SecretsRoleArn": "string"
            },
            "CreatedAt": "string",
            "DomainName": "string",
            "EgressAccessLogs": {
                "LogGroupName": "string"
            },
            "Id": "string",
            "Tags": {"string": "string"}
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `update-packaging-group`

Updates a packaging group's authorization settings.

**Synopsis:**
```bash
aws mediapackage-vod update-packaging-group \
    --id <value> \
    [--authorization <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the packaging group |
| `--authorization` | No | structure | None | Updated CDN authorization credentials |

**Output Schema:**
```json
{
    "ApproximateAssetCount": "integer",
    "Arn": "string",
    "Authorization": {
        "CdnIdentifierSecret": "string",
        "SecretsRoleArn": "string"
    },
    "CreatedAt": "string",
    "DomainName": "string",
    "EgressAccessLogs": {
        "LogGroupName": "string"
    },
    "Id": "string",
    "Tags": {"string": "string"}
}
```

---

### 5.5 `delete-packaging-group`

Deletes a packaging group. All packaging configurations and assets must be deleted first.

**Synopsis:**
```bash
aws mediapackage-vod delete-packaging-group \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the packaging group to delete |

**Output:** None

---

### 5.6 `configure-logs`

Configures egress access logging for a packaging group.

**Synopsis:**
```bash
aws mediapackage-vod configure-logs \
    --id <value> \
    [--egress-access-logs <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the packaging group |
| `--egress-access-logs` | No | structure | None | Egress access logging configuration |

**EgressAccessLogs:**
```json
{
    "LogGroupName": "/aws/mediapackage-vod/my-group"
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "Authorization": {
        "CdnIdentifierSecret": "string",
        "SecretsRoleArn": "string"
    },
    "CreatedAt": "string",
    "DomainName": "string",
    "EgressAccessLogs": {
        "LogGroupName": "string"
    },
    "Id": "string",
    "Tags": {"string": "string"}
}
```
