# Groups

### 2.1 `create-group`

Creates a group that can be used to associate canaries together for reporting and management.

**Synopsis:**
```bash
aws synthetics create-group \
    --name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The name of the group (1-64 chars) |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "Group": {
        "Id": "string",
        "Name": "string",
        "Arn": "string",
        "Tags": {
            "string": "string"
        },
        "CreatedTime": "timestamp",
        "LastModifiedTime": "timestamp"
    }
}
```

---

### 2.2 `delete-group`

Deletes a group. The group is not deleted until all associated canaries are removed.

**Synopsis:**
```bash
aws synthetics delete-group \
    --group-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-identifier` | **Yes** | string | -- | The name or ARN of the group to delete |

**Output Schema:**
```json
{}
```

---

### 2.3 `get-group`

Returns information about one group.

**Synopsis:**
```bash
aws synthetics get-group \
    --group-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-identifier` | **Yes** | string | -- | The name or ARN of the group |

**Output Schema:**
```json
{
    "Group": {
        "Id": "string",
        "Name": "string",
        "Arn": "string",
        "Tags": {
            "string": "string"
        },
        "CreatedTime": "timestamp",
        "LastModifiedTime": "timestamp"
    }
}
```

---

### 2.4 `list-groups`

Returns a list of all groups in the account. **Paginated operation.**

**Synopsis:**
```bash
aws synthetics list-groups \
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
| `--page-size` | No | integer | None | Items per API call (max 20) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Groups": [
        {
            "Id": "string",
            "Name": "string",
            "Arn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `associate-resource`

Associates a canary with a group. A canary can be associated with up to 10 groups.

**Synopsis:**
```bash
aws synthetics associate-resource \
    --group-identifier <value> \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-identifier` | **Yes** | string | -- | The name or ARN of the group |
| `--resource-arn` | **Yes** | string | -- | The ARN of the canary to associate |

**Output Schema:**
```json
{}
```

---

### 2.6 `disassociate-resource`

Removes a canary from a group.

**Synopsis:**
```bash
aws synthetics disassociate-resource \
    --group-identifier <value> \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-identifier` | **Yes** | string | -- | The name or ARN of the group |
| `--resource-arn` | **Yes** | string | -- | The ARN of the canary to disassociate |

**Output Schema:**
```json
{}
```

---

### 2.7 `list-group-resources`

Lists the canaries associated with a group. **Paginated operation.**

**Synopsis:**
```bash
aws synthetics list-group-resources \
    --group-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-identifier` | **Yes** | string | -- | The name or ARN of the group |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 20) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Resources": ["string"],
    "NextToken": "string"
}
```

---

### 2.8 `list-associated-groups`

Lists the groups that a canary is associated with. **Paginated operation.**

**Synopsis:**
```bash
aws synthetics list-associated-groups \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the canary |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 20) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Groups": [
        {
            "Id": "string",
            "Name": "string",
            "Arn": "string"
        }
    ],
    "NextToken": "string"
}
```
