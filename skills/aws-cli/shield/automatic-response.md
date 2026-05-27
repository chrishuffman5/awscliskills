# Automatic Response

Application-layer automatic response enables Shield Advanced to automatically create, evaluate, and deploy WAF rules to mitigate application-layer (Layer 7) DDoS attacks.

### 6.1 `enable-application-layer-automatic-response`

Enables Shield Advanced automatic response for application-layer DDoS attacks on a protected resource.

**Synopsis:**
```bash
aws shield enable-application-layer-automatic-response \
    --resource-arn <value> \
    --action <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the protected resource |
| `--action` | **Yes** | structure | -- | Action to take: `Block={}` or `Count={}` |

**Action Structure (one of):**
```json
{
    "Block": {}
}
```
or
```json
{
    "Count": {}
}
```

- `Block`: Automatically block traffic identified as part of a DDoS attack
- `Count`: Count traffic identified as part of a DDoS attack (monitor only)

**Output Schema:** Empty on success.

---

### 6.2 `disable-application-layer-automatic-response`

Disables Shield Advanced automatic response for application-layer attacks on a protected resource.

**Synopsis:**
```bash
aws shield disable-application-layer-automatic-response \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the protected resource |

**Output Schema:** Empty on success.

---

### 6.3 `update-application-layer-automatic-response`

Updates the application-layer automatic response action for a protected resource.

**Synopsis:**
```bash
aws shield update-application-layer-automatic-response \
    --resource-arn <value> \
    --action <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the protected resource |
| `--action` | **Yes** | structure | -- | Updated action: `Block={}` or `Count={}` |

**Output Schema:** Empty on success.
