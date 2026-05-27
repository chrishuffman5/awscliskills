# Notifications

### 12.1 `notify-provision-product-engine-workflow-result`

Notifies the result of the provisioning engine execution for a provision product workflow.

**Synopsis:**
```bash
aws servicecatalog notify-provision-product-engine-workflow-result \
    --workflow-token <value> \
    --record-id <value> \
    --status <value> \
    [--failure-reason <value>] \
    [--resource-identifier <value>] \
    [--outputs <value>] \
    --idempotency-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-token` | **Yes** | string | -- | Workflow token from the engine |
| `--record-id` | **Yes** | string | -- | Record identifier |
| `--status` | **Yes** | string | -- | Status: `SUCCEEDED` or `FAILED` |
| `--failure-reason` | No | string | None | Reason for failure |
| `--resource-identifier` | No | structure | None | Resource identifier. Shorthand: `UniqueTag={Key=string,Value=string}` |
| `--outputs` | No | list | None | Outputs. Shorthand: `OutputKey=string,OutputValue=string,Description=string ...` |
| `--idempotency-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
{}
```

---

### 12.2 `notify-terminate-provisioned-product-engine-workflow-result`

Notifies the result of the provisioning engine execution for a terminate provisioned product workflow.

**Synopsis:**
```bash
aws servicecatalog notify-terminate-provisioned-product-engine-workflow-result \
    --workflow-token <value> \
    --record-id <value> \
    --status <value> \
    [--failure-reason <value>] \
    --idempotency-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-token` | **Yes** | string | -- | Workflow token from the engine |
| `--record-id` | **Yes** | string | -- | Record identifier |
| `--status` | **Yes** | string | -- | Status: `SUCCEEDED` or `FAILED` |
| `--failure-reason` | No | string | None | Reason for failure |
| `--idempotency-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
{}
```

---

### 12.3 `notify-update-provisioned-product-engine-workflow-result`

Notifies the result of the provisioning engine execution for an update provisioned product workflow.

**Synopsis:**
```bash
aws servicecatalog notify-update-provisioned-product-engine-workflow-result \
    --workflow-token <value> \
    --record-id <value> \
    --status <value> \
    [--failure-reason <value>] \
    [--outputs <value>] \
    --idempotency-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workflow-token` | **Yes** | string | -- | Workflow token from the engine |
| `--record-id` | **Yes** | string | -- | Record identifier |
| `--status` | **Yes** | string | -- | Status: `SUCCEEDED` or `FAILED` |
| `--failure-reason` | No | string | None | Reason for failure |
| `--outputs` | No | list | None | Outputs. Shorthand: `OutputKey=string,OutputValue=string,Description=string ...` |
| `--idempotency-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
{}
```
