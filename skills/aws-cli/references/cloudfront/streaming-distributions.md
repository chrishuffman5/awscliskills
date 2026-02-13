# Streaming Distributions (Legacy)

> **Note:** RTMP streaming distributions are a legacy feature. Use standard distributions for media delivery.

### 16.1 `create-streaming-distribution`

Creates an RTMP streaming distribution.

**Synopsis:**
```bash
aws cloudfront create-streaming-distribution \
    --streaming-distribution-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--streaming-distribution-config` | **Yes** | structure | Streaming distribution configuration |

---

### 16.2 `get-streaming-distribution` / `get-streaming-distribution-config`

Gets a streaming distribution or its configuration.

**Synopsis:**
```bash
aws cloudfront get-streaming-distribution --id <value>
aws cloudfront get-streaming-distribution-config --id <value>
```

---

### 16.3 `list-streaming-distributions`

Lists streaming distributions.

**Synopsis:**
```bash
aws cloudfront list-streaming-distributions \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

---

### 16.4 `update-streaming-distribution`

Updates a streaming distribution.

**Synopsis:**
```bash
aws cloudfront update-streaming-distribution \
    --id <value> \
    --streaming-distribution-config <value> \
    --if-match <value>
```

---

### 16.5 `delete-streaming-distribution`

Deletes a streaming distribution.

**Synopsis:**
```bash
aws cloudfront delete-streaming-distribution \
    --id <value> \
    --if-match <value>
```

---
