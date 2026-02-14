# Objects (Data Plane)

All `mediastore-data` commands require the `--endpoint` option specifying the container's data endpoint URL. Retrieve the endpoint with `aws mediastore describe-container --container-name <name> --query 'Container.Endpoint' --output text`.

### 4.1 `put-object`

Uploads an object to a MediaStore container.

**Synopsis:**
```bash
aws mediastore-data put-object \
    --endpoint <value> \
    --body <value> \
    --path <value> \
    [--content-type <value>] \
    [--cache-control <value>] \
    [--storage-class <value>] \
    [--upload-availability <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint` | **Yes** | string | -- | Container data endpoint URL |
| `--body` | **Yes** | streaming blob | -- | File path to upload (no `file://` prefix) |
| `--path` | **Yes** | string | -- | Object path in container (1-900 chars, max 10 folders deep) |
| `--content-type` | No | string | None | MIME type of the object |
| `--cache-control` | No | string | None | HTTP Cache-Control header value |
| `--storage-class` | No | string | `TEMPORAL` | Storage class: `TEMPORAL` |
| `--upload-availability` | No | string | `STANDARD` | `STANDARD` or `STREAMING` (chunked upload) |

**Constraints:**
- Standard upload: max 25 MB
- Streaming upload: max 10 MB
- Path: max 10 nested folders

**Output Schema:**
```json
{
    "ContentSHA256": "string",
    "ETag": "string",
    "StorageClass": "TEMPORAL"
}
```

---

### 4.2 `get-object`

Downloads an object from a MediaStore container.

**Synopsis:**
```bash
aws mediastore-data get-object \
    --endpoint <value> \
    --path <value> \
    [--range <value>] \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint` | **Yes** | string | -- | Container data endpoint URL |
| `--path` | **Yes** | string | -- | Object path in container |
| `--range` | No | string | None | Byte range to retrieve (e.g., `bytes=0-100`) |
| `<outfile>` | **Yes** | string | -- | Local file path to save the downloaded content |

**Output Schema:**
```json
{
    "Body": "streaming blob",
    "CacheControl": "string",
    "ContentRange": "string",
    "ContentLength": "long",
    "ContentType": "string",
    "ETag": "string",
    "LastModified": "timestamp",
    "StatusCode": "integer"
}
```

---

### 4.3 `describe-object`

Gets metadata for an object without downloading its content.

**Synopsis:**
```bash
aws mediastore-data describe-object \
    --endpoint <value> \
    --path <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint` | **Yes** | string | -- | Container data endpoint URL |
| `--path` | **Yes** | string | -- | Object path in container |

**Output Schema:**
```json
{
    "ETag": "string",
    "ContentType": "string",
    "ContentLength": "long",
    "CacheControl": "string",
    "LastModified": "timestamp"
}
```

---

### 4.4 `list-items`

Lists objects and folders at a path in the container. **Paginated operation.**

**Synopsis:**
```bash
aws mediastore-data list-items \
    --endpoint <value> \
    [--path <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint` | **Yes** | string | -- | Container data endpoint URL |
| `--path` | No | string | `/` | Path in the container to list (0-900 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Number of items per API call |
| `--max-items` | No | integer | None | Total number of items to return |

**Output Schema:**
```json
{
    "Items": [
        {
            "Name": "string",
            "Type": "OBJECT|FOLDER",
            "ETag": "string",
            "LastModified": "timestamp",
            "ContentType": "string",
            "ContentLength": "long"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `delete-object`

Deletes an object from a MediaStore container.

**Synopsis:**
```bash
aws mediastore-data delete-object \
    --endpoint <value> \
    --path <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint` | **Yes** | string | -- | Container data endpoint URL |
| `--path` | **Yes** | string | -- | Object path to delete |

**Output:** None
