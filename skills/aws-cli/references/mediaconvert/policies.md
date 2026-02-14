# Policies

### 5.1 `put-policy`

Creates or updates the input source policy that controls which input sources (HTTP, HTTPS, S3) are allowed for transcoding jobs.

**Synopsis:**
```bash
aws mediaconvert put-policy \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy` | **Yes** | structure | -- | Input source policy configuration |

**Policy structure:**
```json
{
    "HttpInputs": "ALLOWED|DISALLOWED",
    "HttpsInputs": "ALLOWED|DISALLOWED",
    "S3Inputs": "ALLOWED|DISALLOWED"
}
```

**Output Schema:**
```json
{
    "Policy": {
        "HttpInputs": "ALLOWED|DISALLOWED",
        "HttpsInputs": "ALLOWED|DISALLOWED",
        "S3Inputs": "ALLOWED|DISALLOWED"
    }
}
```

---

### 5.2 `get-policy`

Retrieves the current input source policy for the account.

**Synopsis:**
```bash
aws mediaconvert get-policy \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "Policy": {
        "HttpInputs": "ALLOWED|DISALLOWED",
        "HttpsInputs": "ALLOWED|DISALLOWED",
        "S3Inputs": "ALLOWED|DISALLOWED"
    }
}
```

---

### 5.3 `delete-policy`

Deletes the input source policy, restoring default behavior (all input sources allowed).

**Synopsis:**
```bash
aws mediaconvert delete-policy \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output:** None
