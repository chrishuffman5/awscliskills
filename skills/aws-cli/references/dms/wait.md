# Wait

The `aws dms wait` subcommand blocks until a DMS resource reaches a specific state or fails after maximum polling attempts.

### 15.1 `replication-instance-available`

Wait until a replication instance is available. Polls every **60 seconds**, max **60 checks** (up to 60 minutes).

**Synopsis:**
```bash
aws dms wait replication-instance-available \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `replication-instance-arn`, `replication-instance-id`, `replication-instance-class`, `engine-version` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output:** None. Returns 0 on success, 255 on timeout.

---

### 15.2 `replication-instance-deleted`

Wait until a replication instance is deleted. Polls every **15 seconds**, max **60 checks** (up to 15 minutes).

**Synopsis:**
```bash
aws dms wait replication-instance-deleted \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `replication-instance-available`.

**Output:** None. Returns 0 on success, 255 on timeout.

---

### 15.3 `replication-task-ready`

Wait until a replication task is ready. Polls every **15 seconds**, max **60 checks** (up to 15 minutes).

**Synopsis:**
```bash
aws dms wait replication-task-ready \
    [--filters <value>] \
    [--without-settings | --no-without-settings] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `replication-task-arn`, `replication-task-id`, `migration-type`, `endpoint-arn`, `replication-instance-arn` |
| `--without-settings` | No | boolean | false | Omit task settings |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output:** None. Returns 0 on success, 255 on timeout.

---

### 15.4 `replication-task-stopped`

Wait until a replication task is stopped. Polls every **15 seconds**, max **60 checks** (up to 15 minutes).

**Synopsis:**
```bash
aws dms wait replication-task-stopped \
    [--filters <value>] \
    [--without-settings | --no-without-settings] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `replication-task-ready`.

**Output:** None. Returns 0 on success, 255 on timeout.

---

### 15.5 `replication-task-running`

Wait until a replication task is running. Polls every **15 seconds**, max **60 checks** (up to 15 minutes).

**Synopsis:**
```bash
aws dms wait replication-task-running \
    [--filters <value>] \
    [--without-settings | --no-without-settings] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `replication-task-ready`.

**Output:** None. Returns 0 on success, 255 on timeout.

---

### 15.6 `replication-task-deleted`

Wait until a replication task is deleted. Polls every **15 seconds**, max **60 checks** (up to 15 minutes).

**Synopsis:**
```bash
aws dms wait replication-task-deleted \
    [--filters <value>] \
    [--without-settings | --no-without-settings] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `replication-task-ready`.

**Output:** None. Returns 0 on success, 255 on timeout.

---

### 15.7 `endpoint-deleted`

Wait until an endpoint is deleted. Polls every **5 seconds**, max **60 checks** (up to 5 minutes).

**Synopsis:**
```bash
aws dms wait endpoint-deleted \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `endpoint-arn`, `endpoint-type`, `endpoint-id`, `engine-name` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output:** None. Returns 0 on success, 255 on timeout.

---

### 15.8 `test-connection-succeeds`

Wait until a test connection succeeds. Polls every **5 seconds**, max **60 checks** (up to 5 minutes).

**Synopsis:**
```bash
aws dms wait test-connection-succeeds \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `endpoint-arn`, `replication-instance-arn` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output:** None. Returns 0 on success, 255 on timeout.
