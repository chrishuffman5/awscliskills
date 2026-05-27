# Tags

### 5.1 `tag-certificate-authority`

Adds tags to a private CA. Tags are key-value pairs for identification and cost allocation.

**Synopsis:**
```bash
aws acm-pca tag-certificate-authority \
    --certificate-authority-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA to tag |
| `--tags` | **Yes** | list | -- | Tags to add (max 50). Shorthand: `Key=string,Value=string ...` |

**Tag Structure:**
```json
[
    {
        "Key": "string",
        "Value": "string"
    }
]
```

**Output Schema:**

No output fields (empty response on success).

---

### 5.2 `untag-certificate-authority`

Removes tags from a private CA.

**Synopsis:**
```bash
aws acm-pca untag-certificate-authority \
    --certificate-authority-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA to untag |
| `--tags` | **Yes** | list | -- | Tags to remove. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**

No output fields (empty response on success).

---

### 5.3 `list-tags`

Lists tags associated with a private CA. **Paginated operation.**

**Synopsis:**
```bash
aws acm-pca list-tags \
    --certificate-authority-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "NextToken": "string"
}
```
