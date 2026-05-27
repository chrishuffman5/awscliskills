# Domains

### 1.1 `register-domain`

Registers a new SWF domain.

**Synopsis:**
```bash
aws swf register-domain \
    --name <value> \
    --workflow-execution-retention-period-in-days <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Domain name (1-256 chars). Must be unique in the region |
| `--workflow-execution-retention-period-in-days` | **Yes** | string | -- | Retention period for workflow history in days (max 90). Use `NONE` or `0` for no retention |
| `--description` | No | string | None | Domain description (max 1024 chars) |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |

**Output:** None

---

### 1.2 `describe-domain`

Describes a domain including its status and configuration.

**Synopsis:**
```bash
aws swf describe-domain \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Domain name (1-256 chars) |

**Output Schema:**
```json
{
    "domainInfo": {
        "name": "string",
        "status": "REGISTERED|DEPRECATED",
        "description": "string",
        "arn": "string"
    },
    "configuration": {
        "workflowExecutionRetentionPeriodInDays": "string"
    }
}
```

---

### 1.3 `list-domains`

Lists domains by registration status. **Paginated operation.**

**Synopsis:**
```bash
aws swf list-domains \
    --registration-status <value> \
    [--reverse-order | --no-reverse-order] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-status` | **Yes** | string | -- | `REGISTERED` or `DEPRECATED` |
| `--reverse-order` | No | boolean | false | Return results in reverse alphabetical order |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "domainInfos": [
        {
            "name": "string",
            "status": "REGISTERED|DEPRECATED",
            "description": "string",
            "arn": "string"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 1.4 `deprecate-domain`

Deprecates a domain. No new workflow executions can be started in a deprecated domain, but existing ones continue to run.

**Synopsis:**
```bash
aws swf deprecate-domain \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Domain name (1-256 chars) |

**Output:** None

---

### 1.5 `undeprecate-domain`

Undeprecates a previously deprecated domain, making it available for new workflow executions.

**Synopsis:**
```bash
aws swf undeprecate-domain \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Domain name (1-256 chars) |

**Output:** None
