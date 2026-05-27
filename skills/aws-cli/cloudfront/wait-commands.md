# Wait Commands

### 18.1 `wait distribution-deployed`

Waits until a distribution is fully deployed. Polls `get-distribution` every 60 seconds until `Status` is `Deployed`. Times out after 35 attempts (35 minutes).

**Synopsis:**
```bash
aws cloudfront wait distribution-deployed \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Distribution ID |

**Output:** None (exits 0 on success, 255 on timeout).

---

### 18.2 `wait invalidation-completed`

Waits until an invalidation is completed. Polls `get-invalidation` every 20 seconds until `Status` is `Completed`. Times out after 30 attempts (10 minutes).

**Synopsis:**
```bash
aws cloudfront wait invalidation-completed \
    --distribution-id <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--distribution-id` | **Yes** | string | Distribution ID |
| `--id` | **Yes** | string | Invalidation ID |

**Output:** None (exits 0 on success, 255 on timeout).

---

### 18.3 `wait streaming-distribution-deployed`

Waits until a streaming distribution is deployed. Polls every 60 seconds, times out after 25 attempts.

**Synopsis:**
```bash
aws cloudfront wait streaming-distribution-deployed \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Streaming distribution ID |

**Output:** None (exits 0 on success, 255 on timeout).

---
