# Wait Commands

Wait commands for Route 53 ARC via `aws route53-recovery-control-config wait`. These commands poll the API until a resource reaches a specific state.

### 10.1 `wait cluster-created`

Waits until a cluster reaches the `DEPLOYED` status. Polls `describe-cluster` every 5 seconds until successful (max 26 attempts).

**Synopsis:**
```bash
aws route53-recovery-control-config wait cluster-created \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |

**Output:** None. Exits 0 on success, non-zero on failure or timeout.

---

### 10.2 `wait cluster-deleted`

Waits until a cluster is deleted (returns 404). Polls `describe-cluster` every 5 seconds until successful (max 26 attempts).

**Synopsis:**
```bash
aws route53-recovery-control-config wait cluster-deleted \
    --cluster-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |

**Output:** None. Exits 0 on success, non-zero on failure or timeout.

---

### 10.3 `wait control-panel-created`

Waits until a control panel reaches the `DEPLOYED` status. Polls `describe-control-panel` every 5 seconds until successful (max 26 attempts).

**Synopsis:**
```bash
aws route53-recovery-control-config wait control-panel-created \
    --control-panel-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-panel-arn` | **Yes** | string | -- | ARN of the control panel |

**Output:** None. Exits 0 on success, non-zero on failure or timeout.

---

### 10.4 `wait control-panel-deleted`

Waits until a control panel is deleted (returns 404). Polls `describe-control-panel` every 5 seconds until successful (max 26 attempts).

**Synopsis:**
```bash
aws route53-recovery-control-config wait control-panel-deleted \
    --control-panel-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-panel-arn` | **Yes** | string | -- | ARN of the control panel |

**Output:** None. Exits 0 on success, non-zero on failure or timeout.

---

### 10.5 `wait routing-control-created`

Waits until a routing control reaches the `DEPLOYED` status. Polls `describe-routing-control` every 5 seconds until successful (max 26 attempts).

**Synopsis:**
```bash
aws route53-recovery-control-config wait routing-control-created \
    --routing-control-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--routing-control-arn` | **Yes** | string | -- | ARN of the routing control |

**Output:** None. Exits 0 on success, non-zero on failure or timeout.

---

### 10.6 `wait routing-control-deleted`

Waits until a routing control is deleted (returns 404). Polls `describe-routing-control` every 5 seconds until successful (max 26 attempts).

**Synopsis:**
```bash
aws route53-recovery-control-config wait routing-control-deleted \
    --routing-control-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--routing-control-arn` | **Yes** | string | -- | ARN of the routing control |

**Output:** None. Exits 0 on success, non-zero on failure or timeout.
