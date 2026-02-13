# Aliases

### 8.1 `create-alias`

Creates an alias for a fleet. Aliases provide a layer of indirection for game session placement.

**Synopsis:**
```bash
aws gamelift create-alias \
    --name <value> \
    --routing-strategy <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Descriptive label (1-1024 chars) |
| `--routing-strategy` | **Yes** | structure | -- | Routing config. Shorthand: `Type=SIMPLE\|TERMINAL,FleetId=string,Message=string` |
| `--description` | No | string | None | Description (1-1024 chars) |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "Alias": {
        "AliasId": "string",
        "Name": "string",
        "AliasArn": "string",
        "Description": "string",
        "RoutingStrategy": {
            "Type": "SIMPLE|TERMINAL",
            "FleetId": "string",
            "Message": "string"
        },
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp"
    }
}
```

---

### 8.2 `delete-alias`

Deletes a fleet alias.

**Synopsis:**
```bash
aws gamelift delete-alias \
    --alias-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-id` | **Yes** | string | -- | Alias ID or ARN |

**Output Schema:**
```json
None
```

---

### 8.3 `describe-alias`

Retrieves properties of an alias.

**Synopsis:**
```bash
aws gamelift describe-alias \
    --alias-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-id` | **Yes** | string | -- | Alias ID or ARN |

**Output Schema:**
```json
{
    "Alias": {
        "AliasId": "string",
        "Name": "string",
        "AliasArn": "string",
        "Description": "string",
        "RoutingStrategy": {
            "Type": "SIMPLE|TERMINAL",
            "FleetId": "string",
            "Message": "string"
        },
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp"
    }
}
```

---

### 8.4 `list-aliases`

Retrieves all aliases in the account. **Paginated.**

**Synopsis:**
```bash
aws gamelift list-aliases \
    [--routing-strategy-type <value>] \
    [--name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--routing-strategy-type` | No | string | None | Filter: `SIMPLE` or `TERMINAL` |
| `--name` | No | string | None | Filter by name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Aliases": [
        {
            "AliasId": "string",
            "Name": "string",
            "AliasArn": "string",
            "Description": "string",
            "RoutingStrategy": {
                "Type": "SIMPLE|TERMINAL",
                "FleetId": "string",
                "Message": "string"
            },
            "CreationTime": "timestamp",
            "LastUpdatedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `update-alias`

Updates alias properties including name, description, and routing strategy.

**Synopsis:**
```bash
aws gamelift update-alias \
    --alias-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--routing-strategy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-id` | **Yes** | string | -- | Alias ID or ARN |
| `--name` | No | string | None | New name |
| `--description` | No | string | None | New description |
| `--routing-strategy` | No | structure | None | New routing. Shorthand: `Type=SIMPLE\|TERMINAL,FleetId=string,Message=string` |

**Output Schema:**
```json
{
    "Alias": {
        "AliasId": "string",
        "Name": "string",
        "AliasArn": "string",
        "Description": "string",
        "RoutingStrategy": {
            "Type": "SIMPLE|TERMINAL",
            "FleetId": "string",
            "Message": "string"
        },
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp"
    }
}
```

---

### 8.6 `resolve-alias`

Retrieves the fleet ID associated with an alias.

**Synopsis:**
```bash
aws gamelift resolve-alias \
    --alias-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-id` | **Yes** | string | -- | Alias ID or ARN |

**Output Schema:**
```json
{
    "FleetId": "string",
    "FleetArn": "string"
}
```
