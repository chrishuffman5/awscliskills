# Wait Commands

Wait commands for Transfer Family via `aws transfer wait`. These commands poll the API until a server reaches a specific state.

### 12.1 `wait server-online`

Waits until a server reaches the `ONLINE` state. Polls `describe-server` every 30 seconds until successful (max 120 attempts = 60 minutes).

**Synopsis:**
```bash
aws transfer wait server-online \
    --server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |

**Output:** None. Exits 0 on success, non-zero on failure or timeout.

---

### 12.2 `wait server-offline`

Waits until a server reaches the `OFFLINE` state. Polls `describe-server` every 30 seconds until successful (max 120 attempts = 60 minutes).

**Synopsis:**
```bash
aws transfer wait server-offline \
    --server-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-id` | **Yes** | string | -- | Server ID |

**Output:** None. Exits 0 on success, non-zero on failure or timeout.
