# Applications

### 3.1 `create-application`

Creates an application grouping for discovered configuration items.

**Synopsis:**
```bash
aws discovery create-application \
    --name <value> \
    [--description <value>] \
    [--wave <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Application name (max 127 chars) |
| `--description` | No | string | None | Application description (max 1000 chars) |
| `--wave` | No | string | None | Migration wave name (max 256 chars) |

**Output Schema:**
```json
{
    "configurationId": "string"
}
```

---

### 3.2 `update-application`

Updates an existing application's metadata.

**Synopsis:**
```bash
aws discovery update-application \
    --configuration-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-id` | **Yes** | string | -- | Application configuration ID |
| `--name` | No | string | None | New application name (max 127 chars) |
| `--description` | No | string | None | New description (max 1000 chars) |

**Output:** None on success.

---

### 3.3 `delete-applications`

Deletes one or more applications.

**Synopsis:**
```bash
aws discovery delete-applications \
    --configuration-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-ids` | **Yes** | list(string) | -- | Application configuration IDs to delete |

**Output:** None on success.

---

### 3.4 `associate-configuration-items-to-application`

Associates configuration items (servers, processes) to an application.

**Synopsis:**
```bash
aws discovery associate-configuration-items-to-application \
    --application-configuration-id <value> \
    --configuration-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-configuration-id` | **Yes** | string | -- | Application configuration ID |
| `--configuration-ids` | **Yes** | list(string) | -- | Configuration IDs to associate |

**Output:** None on success.

---

### 3.5 `disassociate-configuration-items-from-application`

Removes configuration items from an application.

**Synopsis:**
```bash
aws discovery disassociate-configuration-items-from-application \
    --application-configuration-id <value> \
    --configuration-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-configuration-id` | **Yes** | string | -- | Application configuration ID |
| `--configuration-ids` | **Yes** | list(string) | -- | Configuration IDs to disassociate |

**Output:** None on success.
