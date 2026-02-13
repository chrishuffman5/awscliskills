# Graph Queries & Tags (Neptune Analytics)

### 13.1 `execute-query`

Executes a query on a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph execute-query \
    --graph-identifier <value> \
    --query-string <value> \
    --language <value> \
    [--parameters <value>] \
    [--plan-cache <value>] \
    [--explain-mode <value>] \
    [--query-timeout-milliseconds <value>] \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--query-string` | **Yes** | string | -- | Query string |
| `--language` | **Yes** | string | -- | Query language: `OPEN_CYPHER` |
| `--parameters` | No | map | None | Query parameters |
| `--plan-cache` | No | string | `AUTO` | Plan cache: `ENABLED`, `DISABLED`, `AUTO` |
| `--explain-mode` | No | string | -- | Explain mode: `STATIC`, `DETAILS` |
| `--query-timeout-milliseconds` | No | integer | -- | Query timeout in milliseconds |
| `outfile` | **Yes** | string | -- | Output file path for results |

**Output:** Binary payload written to `outfile` (JSON format).

---

### 13.2 `cancel-query`

Cancels a running query on a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph cancel-query \
    --graph-identifier <value> \
    --query-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--query-id` | **Yes** | string | -- | Query ID to cancel |

**Output:** None

---

### 13.3 `get-query`

Gets details about a running query on a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph get-query \
    --graph-identifier <value> \
    --query-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--query-id` | **Yes** | string | -- | Query ID |

**Output Schema:**
```json
{
    "id": "string",
    "queryString": "string",
    "waited": "integer",
    "elapsed": "integer",
    "state": "string"
}
```

---

### 13.4 `list-queries`

Lists running queries on a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph list-queries \
    --graph-identifier <value> \
    --max-results <value> \
    [--state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--max-results` | **Yes** | integer | -- | Max number of results |
| `--state` | No | string | -- | Filter by state: `ALL`, `RUNNING`, `WAITING`, `CANCELLING` |

**Output Schema:**
```json
{
    "queries": [
        {
            "id": "string",
            "queryString": "string",
            "waited": "integer",
            "elapsed": "integer",
            "state": "string"
        }
    ]
}
```

---

### 13.5 `tag-resource`

Adds tags to a Neptune Analytics resource.

**Synopsis:**
```bash
aws neptune-graph tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | map | -- | Tags as key-value pairs |

**Output:** None

---

### 13.6 `untag-resource`

Removes tags from a Neptune Analytics resource.

**Synopsis:**
```bash
aws neptune-graph untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 13.7 `list-tags-for-resource`

Lists tags for a Neptune Analytics resource.

**Synopsis:**
```bash
aws neptune-graph list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```
