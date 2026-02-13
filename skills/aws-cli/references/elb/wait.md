# Wait Commands

The `aws elb wait` commands poll the `describe-instance-health` API until a desired state is reached or until a maximum number of checks has been made. Polling occurs every 15 seconds, with a maximum of 40 attempts (10 minutes).

---

### 7.1 `wait any-instance-in-service`

Waits until at least one instance registered with the specified load balancer is in the `InService` state.

**Synopsis:**
```bash
aws elb wait any-instance-in-service \
    --load-balancer-name <value> \
    [--instances <value>] \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--instances` | No | list(string) | None | Specific instance IDs to check; omit to check all |

**Output Schema:**
No output on success. Returns exit code 0 when the condition is met, or exit code 255 on timeout.

---

### 7.2 `wait instance-deregistered`

Waits until the specified instances are deregistered from the load balancer (i.e., no longer returned in `describe-instance-health`).

**Synopsis:**
```bash
aws elb wait instance-deregistered \
    --load-balancer-name <value> \
    [--instances <value>] \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--instances` | No | list(string) | None | Specific instance IDs to check; omit to check all |

**Output Schema:**
No output on success. Returns exit code 0 when the condition is met, or exit code 255 on timeout.

---

### 7.3 `wait instance-in-service`

Waits until all specified instances registered with the load balancer are in the `InService` state.

**Synopsis:**
```bash
aws elb wait instance-in-service \
    --load-balancer-name <value> \
    [--instances <value>] \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--load-balancer-name` | **Yes** | string | -- | Name of the load balancer |
| `--instances` | No | list(string) | None | Specific instance IDs to check; omit to check all |

**Output Schema:**
No output on success. Returns exit code 0 when the condition is met, or exit code 255 on timeout.
