# Tags

## IVS (Low-Latency Streaming)

### 13.1 `tag-resource` (ivs)

Adds tags to an IVS resource.

**Synopsis:**
```bash
aws ivs tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | map | -- | Key-value tag pairs (max 50) |

**Output:** None

---

### 13.2 `untag-resource` (ivs)

Removes tags from an IVS resource.

**Synopsis:**
```bash
aws ivs untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None

---

### 13.3 `list-tags-for-resource` (ivs)

Lists tags for an IVS resource.

**Synopsis:**
```bash
aws ivs list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "tags": {"string": "string"}
}
```

---

## IVS Real-Time

### 13.4 `tag-resource` / `untag-resource` / `list-tags-for-resource` (ivs-realtime)

Same interface as the IVS commands above, using the `aws ivs-realtime` service prefix.

```bash
aws ivs-realtime tag-resource --resource-arn <value> --tags <value>
aws ivs-realtime untag-resource --resource-arn <value> --tag-keys <value>
aws ivs-realtime list-tags-for-resource --resource-arn <value>
```

---

## IVS Chat

### 13.5 `tag-resource` / `untag-resource` / `list-tags-for-resource` (ivschat)

Same interface as the IVS commands above, using the `aws ivschat` service prefix.

```bash
aws ivschat tag-resource --resource-arn <value> --tags <value>
aws ivschat untag-resource --resource-arn <value> --tag-keys <value>
aws ivschat list-tags-for-resource --resource-arn <value>
```
