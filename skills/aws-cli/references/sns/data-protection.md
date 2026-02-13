# Data Protection

### 10.1 `put-data-protection-policy`

Adds or updates an inline data protection policy on a topic. Controls what sensitive data identifiers are allowed or denied in published messages.

**Synopsis:**
```bash
aws sns put-data-protection-policy \
    --resource-arn <value> \
    --data-protection-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the SNS topic |
| `--data-protection-policy` | **Yes** | string | -- | JSON policy document. Max 30,720 chars. Supports `file://` prefix |

**Output Schema:** None

---

### 10.2 `get-data-protection-policy`

Retrieves the data protection policy for a topic.

**Synopsis:**
```bash
aws sns get-data-protection-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the SNS topic |

**Output Schema:**
```json
{
    "DataProtectionPolicy": "string (JSON)"
}
```
