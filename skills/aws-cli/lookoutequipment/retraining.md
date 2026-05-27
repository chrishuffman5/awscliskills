# Retraining

### 5.1 `create-retraining-scheduler`

Creates a retraining scheduler that automatically retrains a model on new data.

**Synopsis:**
```bash
aws lookoutequipment create-retraining-scheduler \
    --model-name <value> \
    --retraining-frequency <value> \
    --lookback-window <value> \
    [--retraining-start-date <value>] \
    [--promote-mode <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model |
| `--retraining-frequency` | **Yes** | string | -- | ISO 8601 duration (min P30D, max P1Y) |
| `--lookback-window` | **Yes** | string | -- | Historical data window: `P180D`, `P360D`, `P540D`, or `P720D` |
| `--retraining-start-date` | No | timestamp | None | Start date for retraining (truncated to UTC day) |
| `--promote-mode` | No | string | None | `MANAGED` (auto-promote) or `MANUAL` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ModelName": "string",
    "ModelArn": "string",
    "Status": "PENDING|RUNNING|STOPPING|STOPPED"
}
```

---

### 5.2 `describe-retraining-scheduler`

Describes a retraining scheduler.

**Synopsis:**
```bash
aws lookoutequipment describe-retraining-scheduler \
    --model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model |

**Output Schema:**
```json
{
    "ModelName": "string",
    "ModelArn": "string",
    "RetrainingStartDate": "timestamp",
    "RetrainingFrequency": "string",
    "LookbackWindow": "P180D|P360D|P540D|P720D",
    "Status": "PENDING|RUNNING|STOPPING|STOPPED",
    "PromoteMode": "MANAGED|MANUAL",
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp"
}
```

---

### 5.3 `list-retraining-schedulers`

Lists retraining schedulers. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutequipment list-retraining-schedulers \
    [--model-name-begins-with <value>] \
    [--status <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name-begins-with` | No | string | None | Filter by model name prefix |
| `--status` | No | string | None | Filter: `PENDING`, `RUNNING`, `STOPPING`, `STOPPED` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-500) |

**Output Schema:**
```json
{
    "NextToken": "string",
    "RetrainingSchedulerSummaries": [
        {
            "ModelName": "string",
            "ModelArn": "string",
            "Status": "PENDING|RUNNING|STOPPING|STOPPED",
            "RetrainingStartDate": "timestamp",
            "RetrainingFrequency": "string",
            "LookbackWindow": "string"
        }
    ]
}
```

---

### 5.4 `update-retraining-scheduler`

Updates a retraining scheduler. Scheduler must be stopped.

**Synopsis:**
```bash
aws lookoutequipment update-retraining-scheduler \
    --model-name <value> \
    [--retraining-start-date <value>] \
    [--retraining-frequency <value>] \
    [--lookback-window <value>] \
    [--promote-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model |
| `--retraining-start-date` | No | timestamp | None | Updated start date |
| `--retraining-frequency` | No | string | None | Updated frequency (ISO 8601, min P30D, max P1Y) |
| `--lookback-window` | No | string | None | Updated lookback: `P180D`, `P360D`, `P540D`, `P720D` |
| `--promote-mode` | No | string | None | Updated mode: `MANAGED` or `MANUAL` |

**Output:** None

---

### 5.5 `delete-retraining-scheduler`

Deletes a retraining scheduler. Scheduler must be stopped.

**Synopsis:**
```bash
aws lookoutequipment delete-retraining-scheduler \
    --model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model |

**Output:** None

---

### 5.6 `start-retraining-scheduler`

Starts a retraining scheduler.

**Synopsis:**
```bash
aws lookoutequipment start-retraining-scheduler \
    --model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model |

**Output Schema:**
```json
{
    "ModelName": "string",
    "ModelArn": "string",
    "Status": "PENDING|RUNNING|STOPPING|STOPPED"
}
```

---

### 5.7 `stop-retraining-scheduler`

Stops a retraining scheduler.

**Synopsis:**
```bash
aws lookoutequipment stop-retraining-scheduler \
    --model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model |

**Output Schema:**
```json
{
    "ModelName": "string",
    "ModelArn": "string",
    "Status": "PENDING|RUNNING|STOPPING|STOPPED"
}
```
