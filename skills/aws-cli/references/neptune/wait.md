# Wait Commands

## Neptune Database Waiters (`aws neptune wait`)

### 14.1 `wait db-instance-available`

Waits until a Neptune DB instance is available. Polls `describe-db-instances` every 30 seconds until `DBInstanceStatus` is `available`. Exits with return code 255 after 60 failed checks.

**Synopsis:**
```bash
aws neptune wait db-instance-available \
    [--db-instance-identifier <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | No | string | -- | Instance identifier to wait for |
| `--filters` | No | list | None | Filters |

**Polling:** Every 30 seconds, max 60 attempts (up to 30 minutes).

---

### 14.2 `wait db-instance-deleted`

Waits until a Neptune DB instance is deleted. Polls `describe-db-instances` every 30 seconds until a 404 response is received. Exits with return code 255 after 60 failed checks.

**Synopsis:**
```bash
aws neptune wait db-instance-deleted \
    [--db-instance-identifier <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-instance-identifier` | No | string | -- | Instance identifier to wait for |
| `--filters` | No | list | None | Filters |

**Polling:** Every 30 seconds, max 60 attempts (up to 30 minutes).

---

## Neptune Analytics Waiters (`aws neptune-graph wait`)

### 14.3 `wait graph-available`

Waits until a Neptune Analytics graph is available. Polls `get-graph` every 60 seconds until `status` is `AVAILABLE`. Exits with return code 255 after 480 failed checks.

**Synopsis:**
```bash
aws neptune-graph wait graph-available \
    --graph-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |

**Polling:** Every 60 seconds, max 480 attempts (up to 8 hours).

---

### 14.4 `wait graph-deleted`

Waits until a Neptune Analytics graph is deleted. Polls `get-graph` every 60 seconds until a 404 response is received. Exits with return code 255 after 60 failed checks.

**Synopsis:**
```bash
aws neptune-graph wait graph-deleted \
    --graph-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |

**Polling:** Every 60 seconds, max 60 attempts (up to 1 hour).

---

### 14.5 `wait graph-snapshot-available`

Waits until a Neptune Analytics graph snapshot is available. Polls `get-graph-snapshot` every 60 seconds until `status` is `AVAILABLE`. Exits with return code 255 after 60 failed checks.

**Synopsis:**
```bash
aws neptune-graph wait graph-snapshot-available \
    --snapshot-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-identifier` | **Yes** | string | -- | Snapshot ID |

**Polling:** Every 60 seconds, max 60 attempts (up to 1 hour).

---

### 14.6 `wait graph-snapshot-deleted`

Waits until a Neptune Analytics graph snapshot is deleted. Polls `get-graph-snapshot` every 60 seconds until a 404 response is received. Exits with return code 255 after 60 failed checks.

**Synopsis:**
```bash
aws neptune-graph wait graph-snapshot-deleted \
    --snapshot-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-identifier` | **Yes** | string | -- | Snapshot ID |

**Polling:** Every 60 seconds, max 60 attempts (up to 1 hour).

---

### 14.7 `wait graph-stopped`

Waits until a Neptune Analytics graph is stopped. Polls `get-graph` every 60 seconds until `status` is `STOPPED`. Exits with return code 255 after 60 failed checks.

**Synopsis:**
```bash
aws neptune-graph wait graph-stopped \
    --graph-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |

**Polling:** Every 60 seconds, max 60 attempts (up to 1 hour).

---

### 14.8 `wait import-task-successful`

Waits until a Neptune Analytics import task succeeds. Polls `get-import-task` every 60 seconds until `status` is `SUCCEEDED`. Exits with return code 255 after 480 failed checks.

**Synopsis:**
```bash
aws neptune-graph wait import-task-successful \
    --task-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-identifier` | **Yes** | string | -- | Import task ID |

**Polling:** Every 60 seconds, max 480 attempts (up to 8 hours).

---

### 14.9 `wait import-task-cancelled`

Waits until a Neptune Analytics import task is cancelled. Polls `get-import-task` every 60 seconds until `status` is `CANCELLED`. Exits with return code 255 after 60 failed checks.

**Synopsis:**
```bash
aws neptune-graph wait import-task-cancelled \
    --task-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-identifier` | **Yes** | string | -- | Import task ID |

**Polling:** Every 60 seconds, max 60 attempts (up to 1 hour).

---

### 14.10 `wait export-task-successful`

Waits until a Neptune Analytics export task succeeds. Polls `get-export-task` every 60 seconds until `status` is `SUCCEEDED`. Exits with return code 255 after 480 failed checks.

**Synopsis:**
```bash
aws neptune-graph wait export-task-successful \
    --task-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-identifier` | **Yes** | string | -- | Export task ID |

**Polling:** Every 60 seconds, max 480 attempts (up to 8 hours).

---

### 14.11 `wait export-task-cancelled`

Waits until a Neptune Analytics export task is cancelled. Polls `get-export-task` every 60 seconds until `status` is `CANCELLED`. Exits with return code 255 after 60 failed checks.

**Synopsis:**
```bash
aws neptune-graph wait export-task-cancelled \
    --task-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-identifier` | **Yes** | string | -- | Export task ID |

**Polling:** Every 60 seconds, max 60 attempts (up to 1 hour).

---

### 14.12 `wait private-graph-endpoint-available`

Waits until a Neptune Analytics private endpoint is available. Polls `get-private-graph-endpoint` every 10 seconds until `status` is `AVAILABLE`. Exits with return code 255 after 180 failed checks.

**Synopsis:**
```bash
aws neptune-graph wait private-graph-endpoint-available \
    --graph-identifier <value> \
    --vpc-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--vpc-id` | **Yes** | string | -- | VPC ID |

**Polling:** Every 10 seconds, max 180 attempts (up to 30 minutes).

---

### 14.13 `wait private-graph-endpoint-deleted`

Waits until a Neptune Analytics private endpoint is deleted. Polls `get-private-graph-endpoint` every 10 seconds until a 404 response is received. Exits with return code 255 after 180 failed checks.

**Synopsis:**
```bash
aws neptune-graph wait private-graph-endpoint-deleted \
    --graph-identifier <value> \
    --vpc-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--vpc-id` | **Yes** | string | -- | VPC ID |

**Polling:** Every 10 seconds, max 180 attempts (up to 30 minutes).
