# Applications

### 1.1 `create-application`

Creates an application in AppConfig. An application is a logical unit of code that provides capabilities for your customers.

**Synopsis:**
```bash
aws appconfig create-application \
    --name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Application name (1-64 chars) |
| `--description` | No | string | None | Application description (0-1024 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "Description": "string"
}
```

---

### 1.2 `get-application`

Retrieves information about an application.

**Synopsis:**
```bash
aws appconfig get-application \
    --application-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID (pattern: `[a-z0-9]{4,7}`) |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "Description": "string"
}
```

---

### 1.3 `list-applications`

Lists all applications. **Paginated operation.**

**Synopsis:**
```bash
aws appconfig list-applications \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Items": [
        {
            "Id": "string",
            "Name": "string",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-application`

Updates an application.

**Synopsis:**
```bash
aws appconfig update-application \
    --application-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--name` | No | string | None | Updated name (1-64 chars) |
| `--description` | No | string | None | Updated description (0-1024 chars) |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "Description": "string"
}
```

---

### 1.5 `delete-application`

Deletes an application. Deleting a configuration does not delete a configuration from a host.

**Synopsis:**
```bash
aws appconfig delete-application \
    --application-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID to delete |

**Output:** None
