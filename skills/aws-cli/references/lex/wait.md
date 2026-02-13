# Wait

The `aws lexv2-models wait` commands block until a resource reaches a specific state. Each waiter polls the resource at regular intervals until the desired state is reached or a maximum number of attempts is exceeded.

### 15.1 `wait bot-available`

Waits until a bot reaches the `Available` status.

**Synopsis:**
```bash
aws lexv2-models wait bot-available \
    --bot-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |

**Output:** None (blocks until bot is available or times out)

---

### 15.2 `wait bot-alias-available`

Waits until a bot alias reaches the `Available` status.

**Synopsis:**
```bash
aws lexv2-models wait bot-alias-available \
    --bot-alias-id <value> \
    --bot-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-alias-id` | **Yes** | string | -- | Alias identifier (10 chars) |
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |

**Output:** None (blocks until alias is available or times out)

---

### 15.3 `wait bot-locale-built`

Waits until a bot locale reaches the `Built` status after a build operation.

**Synopsis:**
```bash
aws lexv2-models wait bot-locale-built \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |

**Output:** None (blocks until locale is built or times out)

---

### 15.4 `wait bot-locale-express-testing-available`

Waits until a bot locale reaches the `ReadyExpressTesting` status.

**Synopsis:**
```bash
aws lexv2-models wait bot-locale-express-testing-available \
    --bot-id <value> \
    --bot-version <value> \
    --locale-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version |
| `--locale-id` | **Yes** | string | -- | Locale identifier |

**Output:** None (blocks until locale is ready for express testing or times out)

---

### 15.5 `wait bot-version-available`

Waits until a bot version reaches the `Available` status.

**Synopsis:**
```bash
aws lexv2-models wait bot-version-available \
    --bot-id <value> \
    --bot-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bot-id` | **Yes** | string | -- | Bot identifier (10 chars) |
| `--bot-version` | **Yes** | string | -- | Bot version number |

**Output:** None (blocks until version is available or times out)

---

### 15.6 `wait bot-export-completed`

Waits until an export reaches the `Completed` status.

**Synopsis:**
```bash
aws lexv2-models wait bot-export-completed \
    --export-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--export-id` | **Yes** | string | -- | Export identifier (10 chars) |

**Output:** None (blocks until export is completed or times out)

---

### 15.7 `wait bot-import-completed`

Waits until an import reaches the `Completed` status.

**Synopsis:**
```bash
aws lexv2-models wait bot-import-completed \
    --import-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--import-id` | **Yes** | string | -- | Import identifier (10 chars) |

**Output:** None (blocks until import is completed or times out)
