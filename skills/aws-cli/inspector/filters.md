# Filters

### 3.1 `create-filter`

Creates a filter resource to define criteria for findings. Filters can suppress findings matching specified criteria.

**Synopsis:**
```bash
aws inspector2 create-filter \
    --action <value> \
    --filter-criteria <value> \
    --name <value> \
    [--description <value>] \
    [--reason <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action` | **Yes** | string | -- | Action for matching findings: `NONE`, `SUPPRESS` |
| `--filter-criteria` | **Yes** | structure | -- | Filter criteria (JSON). Same structure as `list-findings --filter-criteria` |
| `--name` | **Yes** | string | -- | Filter name (1-128 chars) |
| `--description` | No | string | None | Description (1-512 chars) |
| `--reason` | No | string | None | Reason for creating the filter (1-512 chars) |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "arn": "string"
}
```

---

### 3.2 `delete-filter`

Deletes a filter resource.

**Synopsis:**
```bash
aws inspector2 delete-filter \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the filter to delete |

**Output Schema:**
```json
{
    "arn": "string"
}
```

---

### 3.3 `update-filter`

Updates an existing filter resource.

**Synopsis:**
```bash
aws inspector2 update-filter \
    --filter-arn <value> \
    [--action <value>] \
    [--description <value>] \
    [--filter-criteria <value>] \
    [--name <value>] \
    [--reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-arn` | **Yes** | string | -- | ARN of the filter to update |
| `--action` | No | string | None | Updated action: `NONE`, `SUPPRESS` |
| `--description` | No | string | None | Updated description |
| `--filter-criteria` | No | structure | None | Updated filter criteria |
| `--name` | No | string | None | Updated name |
| `--reason` | No | string | None | Updated reason |

**Output Schema:**
```json
{
    "arn": "string"
}
```

---

### 3.4 `list-filters`

Lists all filters in the account. **Paginated.**

**Synopsis:**
```bash
aws inspector2 list-filters \
    [--arns <value>] \
    [--action <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arns` | No | list(string) | None | Filter ARNs to retrieve |
| `--action` | No | string | None | Filter by action: `NONE`, `SUPPRESS` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "filters": [
        {
            "arn": "string",
            "ownerId": "string",
            "name": "string",
            "description": "string",
            "action": "NONE|SUPPRESS",
            "criteria": {},
            "reason": "string",
            "tags": {"key": "value"},
            "createdAt": "timestamp",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
