# Access Logging

### 3.1 `start-access-logging`

Enables access logging for a container. Access logs are delivered to CloudWatch Logs.

**Synopsis:**
```bash
aws mediastore start-access-logging \
    --container-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container (1-255 chars) |

**Output:** None

---

### 3.2 `stop-access-logging`

Disables access logging for a container.

**Synopsis:**
```bash
aws mediastore stop-access-logging \
    --container-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container (1-255 chars) |

**Output:** None
