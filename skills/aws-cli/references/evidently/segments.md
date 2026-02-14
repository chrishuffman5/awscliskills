# Segments

### 5.1 `create-segment`

Creates an audience segment. Segments define a portion of your audience based on user attributes, used to target experiments and launches.

**Synopsis:**
```bash
aws evidently create-segment \
    --name <value> \
    --pattern <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Segment name (1-64 chars, pattern: `^[-a-zA-Z0-9._]*$`) |
| `--pattern` | **Yes** | string | -- | Segment pattern for evaluating user attributes (1-1024 chars) |
| `--description` | No | string | None | Description (0-160 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**Pattern example:**
```json
{"location":["US","CA"],"plan":["premium"]}
```

**Output Schema:**
```json
{
    "segment": {
        "arn": "string",
        "name": "string",
        "pattern": "string",
        "description": "string",
        "createdTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "experimentCount": "long",
        "launchCount": "long",
        "tags": {}
    }
}
```

---

### 5.2 `get-segment`

Retrieves segment details.

**Synopsis:**
```bash
aws evidently get-segment \
    --segment <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--segment` | **Yes** | string | -- | Segment name or ARN (0-2048 chars) |

**Output Schema:**
```json
{
    "segment": {
        "arn": "string",
        "name": "string",
        "pattern": "string",
        "description": "string",
        "createdTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "experimentCount": "long",
        "launchCount": "long",
        "tags": {}
    }
}
```

---

### 5.3 `list-segments`

Lists all segments. **Paginated operation.**

**Synopsis:**
```bash
aws evidently list-segments \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |

**Output Schema:**
```json
{
    "nextToken": "string",
    "segments": [
        {
            "arn": "string",
            "name": "string",
            "pattern": "string",
            "description": "string",
            "createdTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "experimentCount": "long",
            "launchCount": "long",
            "tags": {}
        }
    ]
}
```

---

### 5.4 `delete-segment`

Deletes a segment. Cannot delete a segment that is in use by experiments or launches.

**Synopsis:**
```bash
aws evidently delete-segment \
    --segment <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--segment` | **Yes** | string | -- | Segment name or ARN |

**Output:** None

---

### 5.5 `test-segment-pattern`

Tests a segment pattern against a provided payload to verify it works as expected.

**Synopsis:**
```bash
aws evidently test-segment-pattern \
    --pattern <value> \
    --payload <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pattern` | **Yes** | string | -- | Segment pattern to test (1-1024 chars) |
| `--payload` | **Yes** | string | -- | JSON payload to test against (0-4096 chars) |

**Output Schema:**
```json
{
    "match": "boolean"
}
```
