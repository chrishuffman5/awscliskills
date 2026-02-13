# Wait Commands

The `aws docdb wait` subcommand blocks until a resource reaches a specific state. Each waiter polls periodically and exits with a return code of 0 when the desired state is reached, or 255 after exceeding the maximum number of attempts.

---

### 11.1 `wait db-instance-available`

Wait until a DocumentDB instance reaches the `available` state. Polls `describe-db-instances` every 30 seconds until the instance status is `available`.

**Synopsis:**
```bash
aws docdb wait db-instance-available \
    [--db-instance-identifier <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | No | string | -- | Instance identifier to wait on |
| `--filters` | No | list | None | Filters |

**Waiter Configuration:**

| Setting | Value |
|---------|-------|
| Delay | 30 seconds |
| Max Attempts | 60 |
| Total Wait Time | Up to 30 minutes |

**Example:**
```bash
aws docdb wait db-instance-available \
  --db-instance-identifier my-docdb-instance
```

---

### 11.2 `wait db-instance-deleted`

Wait until a DocumentDB instance is deleted. Polls `describe-db-instances` every 30 seconds until the instance is no longer found (404 error).

**Synopsis:**
```bash
aws docdb wait db-instance-deleted \
    [--db-instance-identifier <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | No | string | -- | Instance identifier to wait on |
| `--filters` | No | list | None | Filters |

**Waiter Configuration:**

| Setting | Value |
|---------|-------|
| Delay | 30 seconds |
| Max Attempts | 60 |
| Total Wait Time | Up to 30 minutes |

**Example:**
```bash
aws docdb wait db-instance-deleted \
  --db-instance-identifier my-docdb-instance
```
