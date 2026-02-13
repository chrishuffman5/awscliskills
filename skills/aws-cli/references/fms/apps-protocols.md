# Apps & Protocols

### 3.1 `put-apps-list`

Creates or updates an apps list used in Firewall Manager policies.

**Synopsis:**
```bash
aws fms put-apps-list \
    --apps-list <value> \
    [--tag-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--apps-list` | **Yes** | structure | -- | Apps list details (see structure below) |
| `--tag-list` | No | list | None | Tags (max 200) |

**Apps List Structure:**
```json
{
    "ListId": "string",
    "ListName": "string",
    "ListUpdateToken": "string",
    "CreateTime": "timestamp",
    "LastUpdateTime": "timestamp",
    "AppsList": [
        {
            "AppName": "string",
            "Protocol": "string",
            "Port": "long"
        }
    ],
    "PreviousAppsList": {}
}
```

Required fields: `ListName`, `AppsList`

**Output Schema:**
```json
{
    "AppsList": {
        "ListId": "string",
        "ListName": "string",
        "ListUpdateToken": "string",
        "CreateTime": "timestamp",
        "LastUpdateTime": "timestamp",
        "AppsList": [
            {
                "AppName": "string",
                "Protocol": "string",
                "Port": "long"
            }
        ],
        "PreviousAppsList": {}
    },
    "AppsListArn": "string"
}
```

---

### 3.2 `get-apps-list`

Returns an apps list by ID.

**Synopsis:**
```bash
aws fms get-apps-list \
    --list-id <value> \
    [--default-list | --no-default-list] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--list-id` | **Yes** | string | -- | List ID (36 chars) |
| `--default-list` | No | boolean | false | Whether to return the default list |

**Output Schema:**
```json
{
    "AppsList": {
        "ListId": "string",
        "ListName": "string",
        "ListUpdateToken": "string",
        "CreateTime": "timestamp",
        "LastUpdateTime": "timestamp",
        "AppsList": [
            {
                "AppName": "string",
                "Protocol": "string",
                "Port": "long"
            }
        ],
        "PreviousAppsList": {}
    },
    "AppsListArn": "string"
}
```

---

### 3.3 `delete-apps-list`

Deletes an apps list.

**Synopsis:**
```bash
aws fms delete-apps-list \
    --list-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--list-id` | **Yes** | string | -- | List ID to delete |

**Output Schema:** Empty on success.

---

### 3.4 `list-apps-lists`

Returns all apps lists. **Paginated.**

**Synopsis:**
```bash
aws fms list-apps-lists \
    [--default-lists | --no-default-lists] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--default-lists` | No | boolean | false | Include default lists |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AppsLists": [
        {
            "ListArn": "string",
            "ListId": "string",
            "ListName": "string",
            "AppsList": [
                {
                    "AppName": "string",
                    "Protocol": "string",
                    "Port": "long"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `put-protocols-list`

Creates or updates a protocols list used in Firewall Manager policies.

**Synopsis:**
```bash
aws fms put-protocols-list \
    --protocols-list <value> \
    [--tag-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protocols-list` | **Yes** | structure | -- | Protocols list details |
| `--tag-list` | No | list | None | Tags (max 200) |

**Protocols List Structure:**
```json
{
    "ListId": "string",
    "ListName": "string",
    "ListUpdateToken": "string",
    "CreateTime": "timestamp",
    "LastUpdateTime": "timestamp",
    "ProtocolsList": ["string"],
    "PreviousProtocolsList": {}
}
```

Required fields: `ListName`, `ProtocolsList`

**Output Schema:**
```json
{
    "ProtocolsList": {
        "ListId": "string",
        "ListName": "string",
        "ListUpdateToken": "string",
        "CreateTime": "timestamp",
        "LastUpdateTime": "timestamp",
        "ProtocolsList": ["string"],
        "PreviousProtocolsList": {}
    },
    "ProtocolsListArn": "string"
}
```

---

### 3.6 `get-protocols-list`

Returns a protocols list by ID.

**Synopsis:**
```bash
aws fms get-protocols-list \
    --list-id <value> \
    [--default-list | --no-default-list] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--list-id` | **Yes** | string | -- | List ID (36 chars) |
| `--default-list` | No | boolean | false | Whether to return the default list |

**Output Schema:**
```json
{
    "ProtocolsList": {
        "ListId": "string",
        "ListName": "string",
        "ListUpdateToken": "string",
        "CreateTime": "timestamp",
        "LastUpdateTime": "timestamp",
        "ProtocolsList": ["string"],
        "PreviousProtocolsList": {}
    },
    "ProtocolsListArn": "string"
}
```

---

### 3.7 `delete-protocols-list`

Deletes a protocols list.

**Synopsis:**
```bash
aws fms delete-protocols-list \
    --list-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--list-id` | **Yes** | string | -- | List ID to delete |

**Output Schema:** Empty on success.

---

### 3.8 `list-protocols-lists`

Returns all protocols lists. **Paginated.**

**Synopsis:**
```bash
aws fms list-protocols-lists \
    [--default-lists | --no-default-lists] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--default-lists` | No | boolean | false | Include default lists |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ProtocolsLists": [
        {
            "ListArn": "string",
            "ListId": "string",
            "ListName": "string",
            "ProtocolsList": ["string"]
        }
    ],
    "NextToken": "string"
}
```
