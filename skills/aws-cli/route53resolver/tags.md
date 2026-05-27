# Tags

> Tag commands exist in both `route53resolver` and `route53profiles`. The syntax is identical.

### 8.1 `tag-resource`

Adds tags to a Route 53 Resolver or Route 53 Profiles resource.

**Synopsis:**
```bash
# Route 53 Resolver
aws route53resolver tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]

# Route 53 Profiles
aws route53profiles tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The resource ARN (max 255 chars) |
| `--tags` | **Yes** | list | -- | Tags (max 200). Shorthand: `Key=string,Value=string ...` (key: 1-128 chars, value: 0-256 chars) |

**Output Schema:**

No output on success.

---

### 8.2 `untag-resource`

Removes tags from a Route 53 Resolver or Route 53 Profiles resource.

**Synopsis:**
```bash
# Route 53 Resolver
aws route53resolver untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]

# Route 53 Profiles
aws route53profiles untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The resource ARN (max 255 chars) |
| `--tag-keys` | **Yes** | list(string) | -- | The tag keys to remove |

**Output Schema:**

No output on success.

---

### 8.3 `list-tags-for-resource`

Lists the tags for a Route 53 Resolver or Route 53 Profiles resource.

**Synopsis:**
```bash
# Route 53 Resolver
aws route53resolver list-tags-for-resource \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]

# Route 53 Profiles
aws route53profiles list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The resource ARN (max 255 chars) |
| `--starting-token` | No | string | None | Pagination token (route53resolver only) |
| `--page-size` | No | integer | None | Items per API call (route53resolver only) |
| `--max-items` | No | integer | None | Total items to return (route53resolver only) |

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
