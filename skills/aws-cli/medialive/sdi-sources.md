# SDI Sources

### 14.1 `create-sdi-source`

Creates an SDI source for use with MediaLive Anywhere on-premises channels.

**Synopsis:**
```bash
aws medialive create-sdi-source \
    [--mode <value>] \
    [--name <value>] \
    [--request-id <value>] \
    [--tags <value>] \
    [--type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mode` | No | string | None | `QUADRANT` or `INTERLEAVE` |
| `--name` | No | string | None | SDI source name |
| `--request-id` | No | string | Auto | Idempotency token |
| `--tags` | No | map | None | Key-value tag pairs |
| `--type` | No | string | None | `SINGLE` or `QUAD` |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "Mode": "QUADRANT|INTERLEAVE",
    "Type": "SINGLE|QUAD",
    "Inputs": ["string"],
    "State": "IDLE|IN_USE|DELETED",
    "Tags": {}
}
```

---

### 14.2 `describe-sdi-source`

Describes an SDI source.

**Synopsis:**
```bash
aws medialive describe-sdi-source \
    --sdi-source-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sdi-source-id` | **Yes** | string | -- | SDI source ID |

**Output Schema:** Same as `create-sdi-source` output.

---

### 14.3 `update-sdi-source`

Updates an SDI source.

**Synopsis:**
```bash
aws medialive update-sdi-source \
    --sdi-source-id <value> \
    [--mode <value>] \
    [--name <value>] \
    [--type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sdi-source-id` | **Yes** | string | -- | SDI source ID to update |
| `--mode` | No | string | None | Updated mode |
| `--name` | No | string | None | Updated name |
| `--type` | No | string | None | Updated type |

**Output Schema:** Same as `create-sdi-source` output.

---

### 14.4 `delete-sdi-source`

Deletes an SDI source.

**Synopsis:**
```bash
aws medialive delete-sdi-source \
    --sdi-source-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sdi-source-id` | **Yes** | string | -- | SDI source ID to delete |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "State": "DELETED"
}
```

---

### 14.5 `list-sdi-sources`

Lists SDI sources. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-sdi-sources \
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
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "SdiSources": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "Mode": "string",
            "Type": "string",
            "Inputs": ["string"],
            "State": "string"
        }
    ]
}
```
