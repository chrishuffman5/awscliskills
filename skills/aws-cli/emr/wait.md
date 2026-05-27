# Wait Commands

The `aws emr wait` subcommand blocks until a resource reaches a specific state.

---

### 16.1 `wait cluster-running`

Polls `describe-cluster` every 30 seconds until the cluster state is `RUNNING` or `WAITING`. Fails after 60 attempts (30 minutes).

**Synopsis:**
```bash
aws emr wait cluster-running \
    --cluster-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster to wait for |

**Example:**
```bash
aws emr wait cluster-running --cluster-id j-XXXXXXXXXXXXX
```

---

### 16.2 `wait cluster-terminated`

Polls `describe-cluster` every 30 seconds until the cluster state is `TERMINATED`. Fails after 60 attempts (30 minutes).

**Synopsis:**
```bash
aws emr wait cluster-terminated \
    --cluster-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster to wait for |

**Example:**
```bash
aws emr wait cluster-terminated --cluster-id j-XXXXXXXXXXXXX
```

---

### 16.3 `wait step-complete`

Polls `describe-step` every 30 seconds until the step state is `COMPLETED`. Fails after 60 attempts (30 minutes).

**Synopsis:**
```bash
aws emr wait step-complete \
    --cluster-id <value> \
    --step-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--step-id` | **Yes** | string | -- | Step ID to wait for |

**Example:**
```bash
aws emr wait step-complete --cluster-id j-XXXXXXXXXXXXX --step-id s-XXXXXXXXXXXXX
```
