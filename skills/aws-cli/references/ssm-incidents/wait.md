# Wait Commands

The `aws ssm-incidents wait` commands poll the replication set API until a desired state is reached or until a maximum number of checks has been made. Polling occurs every 30 seconds, with a maximum of 5 attempts (2.5 minutes).

---

### 13.1 `wait replication-set-active`

Waits until the replication set is in the `ACTIVE` state.

**Synopsis:**
```bash
aws ssm-incidents wait replication-set-active \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Replication set ARN |

**Output Schema:**
No output on success. Returns exit code 0 when the condition is met, or exit code 255 on timeout.

---

### 13.2 `wait replication-set-deleted`

Waits until the replication set is deleted (returns a `ResourceNotFoundException`).

**Synopsis:**
```bash
aws ssm-incidents wait replication-set-deleted \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Replication set ARN |

**Output Schema:**
No output on success. Returns exit code 0 when the condition is met, or exit code 255 on timeout.
