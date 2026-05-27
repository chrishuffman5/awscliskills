# Tags

### 8.1 `tag-resource`

Adds tags to an IAM Identity Center resource (instance, permission set, or application).

**Synopsis:**
```bash
aws sso-admin tag-resource \
    --instance-arn <value> \
    [--resource-arn <value>] \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--resource-arn` | No | string | None | ARN of the specific resource to tag (permission set or application). If omitted, tags the instance |
| `--tags` | **Yes** | list(structure) | -- | Tags (max 75). Structure: `Key=string,Value=string` |

**Output Schema:**

No output on success (HTTP 200).

---

### 8.2 `untag-resource`

Removes tags from an IAM Identity Center resource.

**Synopsis:**
```bash
aws sso-admin untag-resource \
    --instance-arn <value> \
    [--resource-arn <value>] \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--resource-arn` | No | string | None | ARN of the specific resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**

No output on success (HTTP 200).

---

### 8.3 `list-tags-for-resource`

Lists tags for an IAM Identity Center resource.

**Synopsis:**
```bash
aws sso-admin list-tags-for-resource \
    --instance-arn <value> \
    [--resource-arn <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--resource-arn` | No | string | None | ARN of the specific resource |
| `--starting-token` | No | string | None | Pagination token |
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
