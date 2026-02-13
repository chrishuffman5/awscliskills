# Wait Commands

The `aws cloudformation wait` subcommand blocks until a resource reaches a specific state, polling at regular intervals. Each waiter has a maximum number of attempts before failing.

---

### 13.1 `wait stack-create-complete`

Wait until a stack reaches `CREATE_COMPLETE` status. Polls every 30 seconds, max 120 attempts (60 minutes).

**Synopsis:**
```bash
aws cloudformation wait stack-create-complete \
    --stack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |

**Output:** No output on success. Returns non-zero exit code on failure or timeout.

---

### 13.2 `wait stack-update-complete`

Wait until a stack reaches `UPDATE_COMPLETE` status. Polls every 30 seconds, max 120 attempts (60 minutes).

**Synopsis:**
```bash
aws cloudformation wait stack-update-complete \
    --stack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |

**Output:** No output on success. Returns non-zero exit code on failure or timeout.

---

### 13.3 `wait stack-delete-complete`

Wait until a stack is fully deleted. Polls every 30 seconds, max 120 attempts (60 minutes).

**Synopsis:**
```bash
aws cloudformation wait stack-delete-complete \
    --stack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |

**Output:** No output on success. Returns non-zero exit code on failure or timeout.

---

### 13.4 `wait stack-exists`

Wait until a stack exists. Polls every 5 seconds, max 20 attempts (100 seconds).

**Synopsis:**
```bash
aws cloudformation wait stack-exists \
    --stack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |

**Output:** No output on success. Returns non-zero exit code on failure or timeout.

---

### 13.5 `wait stack-import-complete`

Wait until a stack import reaches `IMPORT_COMPLETE` status. Polls every 30 seconds, max 120 attempts (60 minutes).

**Synopsis:**
```bash
aws cloudformation wait stack-import-complete \
    --stack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |

**Output:** No output on success. Returns non-zero exit code on failure or timeout.

---

### 13.6 `wait stack-rollback-complete`

Wait until a stack rollback reaches `ROLLBACK_COMPLETE` or `UPDATE_ROLLBACK_COMPLETE` status. Polls every 30 seconds, max 120 attempts (60 minutes).

**Synopsis:**
```bash
aws cloudformation wait stack-rollback-complete \
    --stack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |

**Output:** No output on success. Returns non-zero exit code on failure or timeout.

---

### 13.7 `wait change-set-create-complete`

Wait until a change set reaches `CREATE_COMPLETE` status. Polls every 30 seconds, max 120 attempts (60 minutes).

**Synopsis:**
```bash
aws cloudformation wait change-set-create-complete \
    --change-set-name <value> \
    [--stack-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--change-set-name` | **Yes** | string | -- | Change set name or ARN |
| `--stack-name` | No | string | None | Stack name (required if change-set-name is not an ARN) |

**Output:** No output on success. Returns non-zero exit code on failure or timeout.

---

### 13.8 `wait type-registration-complete`

Wait until a type registration reaches `COMPLETE` status. Polls every 30 seconds, max 120 attempts (60 minutes).

**Synopsis:**
```bash
aws cloudformation wait type-registration-complete \
    --registration-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-token` | **Yes** | string | -- | Registration token from `register-type` |

**Output:** No output on success. Returns non-zero exit code on failure or timeout.
