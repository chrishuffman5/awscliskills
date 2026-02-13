# VPC Links

### 9.1 `create-vpc-link`

Creates a VPC link for integrating REST API methods with private resources in a VPC via Network Load Balancers.

**Synopsis:**
```bash
aws apigateway create-vpc-link \
    --name <value> \
    --target-arns <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the VPC link |
| `--target-arns` | **Yes** | list(string) | -- | ARNs of Network Load Balancers (currently limited to one) |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "description": "string",
    "targetArns": ["string"],
    "status": "AVAILABLE|PENDING|DELETING|FAILED",
    "statusMessage": "string",
    "tags": {}
}
```

---

### 9.2 `delete-vpc-link`

Deletes a VPC link.

**Synopsis:**
```bash
aws apigateway delete-vpc-link \
    --vpc-link-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-link-id` | **Yes** | string | -- | ID of the VPC link |

**Output:** None

---

### 9.3 `get-vpc-link`

Gets information about a VPC link.

**Synopsis:**
```bash
aws apigateway get-vpc-link \
    --vpc-link-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-link-id` | **Yes** | string | -- | ID of the VPC link |

**Output Schema:** Same as `create-vpc-link`.

---

### 9.4 `get-vpc-links`

Lists VPC links. **Paginated operation.**

**Synopsis:**
```bash
aws apigateway get-vpc-links \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "id": "string",
            "name": "string",
            "description": "string",
            "targetArns": ["string"],
            "status": "AVAILABLE|PENDING|DELETING|FAILED",
            "statusMessage": "string",
            "tags": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 9.5 `update-vpc-link`

Updates a VPC link using patch operations.

**Synopsis:**
```bash
aws apigateway update-vpc-link \
    --vpc-link-id <value> \
    [--patch-operations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-link-id` | **Yes** | string | -- | ID of the VPC link |
| `--patch-operations` | No | list | None | Patch operations |

**Supported Patch Paths:** `/name`, `/description`

**Output Schema:** Same as `create-vpc-link`.
