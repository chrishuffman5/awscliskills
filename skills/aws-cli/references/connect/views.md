# Views

### 20.1 `create-view`

Creates a view for the specified instance.

**Synopsis:**
```bash
aws connect create-view \
    --instance-id <value> \
    --status <value> \
    --content <value> \
    --name <value> \
    [--client-token <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--status` | **Yes** | string | -- | `PUBLISHED` or `SAVED` |
| `--content` | **Yes** | structure | -- | View content with `Template` and `Actions` |
| `--name` | **Yes** | string | -- | View name (1-255 chars) |
| `--client-token` | No | string | None | Idempotency token (max 500) |
| `--description` | No | string | None | Description (1-4096 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**Content:**
```json
{
    "Template": "string",
    "Actions": ["string"]
}
```

**Output Schema:**
```json
{
    "View": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "Status": "PUBLISHED|SAVED",
        "Type": "CUSTOMER_MANAGED|AWS_MANAGED",
        "Description": "string",
        "Version": "integer",
        "Content": { "InputSchema": "string", "Template": "string", "Actions": [] },
        "Tags": { "key": "value" },
        "CreatedTime": "timestamp",
        "LastModifiedTime": "timestamp",
        "ViewContentSha256": "string"
    }
}
```

---

### 20.2 `describe-view`

Describes a view.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--view-id` | **Yes** | string | -- | View ID |

**Output Schema:** Same as create-view View object.

---

### 20.3 `list-views`

Lists views. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--type` | No | string | None | `CUSTOMER_MANAGED` or `AWS_MANAGED` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

**Output Schema:**
```json
{
    "ViewsSummaryList": [ { "Id": "string", "Arn": "string", "Name": "string", "Type": "string", "Status": "string", "Description": "string" } ],
    "NextToken": "string"
}
```

---

### 20.4 `update-view-content`

Updates view content.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--view-id` | **Yes** | string | -- | View ID |
| `--status` | **Yes** | string | -- | `PUBLISHED` or `SAVED` |
| `--content` | **Yes** | structure | -- | Updated content |

**Output Schema:** Same as create-view View object.

---

### 20.5 `update-view-metadata`

Updates view metadata (name, description).

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--view-id` | **Yes** | string | -- | View ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |

**Output:** None

---

### 20.6 `delete-view`

Deletes a view.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--view-id` | **Yes** | string | -- | View ID |

**Output:** None

---

### 20.7 `create-view-version`

Creates a version of a view.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--view-id` | **Yes** | string | -- | View ID |
| `--version-description` | No | string | None | Version description |
| `--view-content-sha256` | No | string | None | SHA256 for conflict detection |

**Output Schema:**
```json
{
    "View": { "Id": "string", "Arn": "string", "Name": "string", "Version": "integer", "VersionDescription": "string" }
}
```

---

### 20.8 `list-view-versions`

Lists view versions. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--view-id` | **Yes** | string | -- | View ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

---

### 20.9 `delete-view-version`

Deletes a view version.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--view-id` | **Yes** | string | -- | View ID |
| `--view-version` | **Yes** | integer | -- | Version to delete |

**Output:** None

---

### 20.10 `search-views`

Searches views. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-criteria` | No | structure | None | Search criteria |

**Output Schema:**
```json
{
    "Views": [ { "Id": "string", "Arn": "string", "Name": "string", "Type": "string", "Status": "string", "Description": "string" } ],
    "NextToken": "string",
    "ApproximateTotalCount": "long"
}
```
