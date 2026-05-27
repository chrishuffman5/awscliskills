# Tags

### 3.1 `add-tags-to-certificate`

Adds one or more tags to an ACM certificate. Tags are key-value pairs that can be used to organize and identify certificates. A certificate can have a maximum of 50 tags.

**Synopsis:**
```bash
aws acm add-tags-to-certificate \
    --certificate-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-arn` | **Yes** | string | -- | ARN of the certificate |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Tag Structure:**
```json
[
    {
        "Key": "string",
        "Value": "string"
    }
]
```

- **Key**: Tag key (1-128 chars). Required.
- **Value**: Tag value (0-256 chars). Optional.

**Output:** None (HTTP 200 on success)

---

### 3.2 `remove-tags-from-certificate`

Removes one or more tags from an ACM certificate. If a tag key is specified without a value, all tags with that key are removed regardless of value. If both key and value are specified, only the exact match is removed.

**Synopsis:**
```bash
aws acm remove-tags-from-certificate \
    --certificate-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-arn` | **Yes** | string | -- | ARN of the certificate |
| `--tags` | **Yes** | list | -- | Tags to remove. Shorthand: `Key=string,Value=string ...` |

**Output:** None (HTTP 200 on success)

---

### 3.3 `list-tags-for-certificate`

Lists the tags associated with an ACM certificate.

**Synopsis:**
```bash
aws acm list-tags-for-certificate \
    --certificate-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-arn` | **Yes** | string | -- | ARN of the certificate |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
