# Users

### 3.1 `create-user`

Creates a broker user. Changes are applied after broker reboot.

**Synopsis:**
```bash
aws mq create-user \
    --broker-id <value> \
    --username <value> \
    --password <value> \
    [--console-access | --no-console-access] \
    [--groups <value>] \
    [--replication-user | --no-replication-user] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--broker-id` | **Yes** | string | -- | The broker ID |
| `--username` | **Yes** | string | -- | Username (2-100 chars, alphanumeric, dashes, periods, underscores, tildes) |
| `--password` | **Yes** | string | -- | Password (12+ chars, 4+ unique chars, no commas/colons/equals) |
| `--console-access` | No | boolean | false | Enable ActiveMQ web console access (ActiveMQ only) |
| `--groups` | No | list | None | Group memberships (max 20, ActiveMQ only) |
| `--replication-user` | No | boolean | false | Mark as CRDR replication user |

**Output:** None

---

### 3.2 `describe-user`

Describes a broker user including pending changes.

**Synopsis:**
```bash
aws mq describe-user \
    --broker-id <value> \
    --username <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--broker-id` | **Yes** | string | -- | The broker ID |
| `--username` | **Yes** | string | -- | The username |

**Output Schema:**
```json
{
    "BrokerId": "string",
    "ConsoleAccess": boolean,
    "Groups": ["string"],
    "Pending": {
        "ConsoleAccess": boolean,
        "Groups": ["string"],
        "PendingChange": "CREATE|UPDATE|DELETE"
    },
    "Username": "string",
    "ReplicationUser": boolean
}
```

---

### 3.3 `list-users`

Lists all users for a broker. **Paginated operation.**

**Synopsis:**
```bash
aws mq list-users \
    --broker-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--broker-id` | **Yes** | string | -- | The broker ID |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "BrokerId": "string",
    "MaxResults": integer,
    "NextToken": "string",
    "Users": [
        {
            "PendingChange": "CREATE|UPDATE|DELETE",
            "Username": "string"
        }
    ]
}
```

---

### 3.4 `update-user`

Updates a broker user. Changes are applied after broker reboot.

**Synopsis:**
```bash
aws mq update-user \
    --broker-id <value> \
    --username <value> \
    [--console-access | --no-console-access] \
    [--groups <value>] \
    [--password <value>] \
    [--replication-user | --no-replication-user] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--broker-id` | **Yes** | string | -- | The broker ID |
| `--username` | **Yes** | string | -- | The username to update |
| `--console-access` | No | boolean | None | Updated console access (ActiveMQ only) |
| `--groups` | No | list | None | Updated group memberships (ActiveMQ only) |
| `--password` | No | string | None | Updated password |
| `--replication-user` | No | boolean | None | Updated replication user flag |

**Output:** None

---

### 3.5 `delete-user`

Deletes a broker user. Changes are applied after broker reboot.

**Synopsis:**
```bash
aws mq delete-user \
    --broker-id <value> \
    --username <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--broker-id` | **Yes** | string | -- | The broker ID |
| `--username` | **Yes** | string | -- | The username to delete |

**Output:** None
