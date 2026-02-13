# Applications

### 1.1 `create-application`

Creates an application.

**Synopsis:**
```bash
aws deploy create-application \
    --application-name <value> \
    [--compute-platform <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name (max 100 chars) |
| `--compute-platform` | No | string | `Server` | Compute platform: `Server`, `Lambda`, `ECS` |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "applicationId": "string"
}
```

---

### 1.2 `delete-application`

Deletes an application. Also deletes all associated deployment groups, revisions, and deployment configurations.

**Synopsis:**
```bash
aws deploy delete-application \
    --application-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |

**Output Schema:**
```json
{}
```

---

### 1.3 `get-application`

Gets information about an application.

**Synopsis:**
```bash
aws deploy get-application \
    --application-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |

**Output Schema:**
```json
{
    "application": {
        "applicationId": "string",
        "applicationName": "string",
        "createTime": "timestamp",
        "linkedToGitHub": true|false,
        "gitHubAccountName": "string",
        "computePlatform": "Server|Lambda|ECS"
    }
}
```

---

### 1.4 `list-applications`

Lists the applications registered with the user or AWS account. **Paginated operation.**

**Synopsis:**
```bash
aws deploy list-applications \
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
    "applications": ["string"],
    "nextToken": "string"
}
```

---

### 1.5 `update-application`

Changes the name of an application.

**Synopsis:**
```bash
aws deploy update-application \
    [--application-name <value>] \
    [--new-application-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | No | string | None | Current application name |
| `--new-application-name` | No | string | None | New application name |

**Output Schema:**
```json
{}
```

---

### 1.6 `batch-get-applications`

Gets information about one or more applications.

**Synopsis:**
```bash
aws deploy batch-get-applications \
    --application-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-names` | **Yes** | list(string) | -- | Application names (max 100) |

**Output Schema:**
```json
{
    "applicationsInfo": [
        {
            "applicationId": "string",
            "applicationName": "string",
            "createTime": "timestamp",
            "linkedToGitHub": true|false,
            "gitHubAccountName": "string",
            "computePlatform": "Server|Lambda|ECS"
        }
    ]
}
```
