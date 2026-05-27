# Wait

The `aws kinesis wait` subcommand polls the API until a resource reaches a specific state. Each waiter polls every 10 seconds and times out after 18 attempts (3 minutes).

---

### 9.1 `wait stream-exists`

Waits until a Kinesis data stream exists and is in `ACTIVE` status. Polls `describe-stream` every 10 seconds.

**Synopsis:**
```bash
aws kinesis wait stream-exists \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |

*Either `--stream-name` or `--stream-arn` must be provided.

**Behavior:**
- Polls every 10 seconds
- Succeeds when `StreamDescription.StreamStatus` is `ACTIVE`
- Exits with error after 18 failed polls (3 minutes)

**Example:**
```bash
aws kinesis create-stream --stream-name my-stream --shard-count 2
aws kinesis wait stream-exists --stream-name my-stream
echo "Stream is now active"
```

---

### 9.2 `wait stream-not-exists`

Waits until a Kinesis data stream no longer exists. Polls `describe-stream` every 10 seconds.

**Synopsis:**
```bash
aws kinesis wait stream-not-exists \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |

*Either `--stream-name` or `--stream-arn` must be provided.

**Behavior:**
- Polls every 10 seconds
- Succeeds when `describe-stream` returns `ResourceNotFoundException`
- Exits with error after 18 failed polls (3 minutes)

**Example:**
```bash
aws kinesis delete-stream --stream-name my-stream
aws kinesis wait stream-not-exists --stream-name my-stream
echo "Stream has been deleted"
```
