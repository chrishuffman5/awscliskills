# Tags

### 13.1 `tag-resource`

Assigns tags to a Backup resource (backup plan, backup vault, or recovery point).

**Synopsis:**
```bash
aws backup tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Key-value tag pairs |

**Example:**
```bash
aws backup tag-resource \
    --resource-arn arn:aws:backup:us-east-1:123456789012:backup-vault:my-vault \
    --tags Environment=Production,Team=Platform
```

**Output:** None

---

### 13.2 `untag-resource`

Removes tags from a Backup resource. Only supports Backup-native resources (backup plans, vaults, recovery points).

**Synopsis:**
```bash
aws backup untag-resource \
    --resource-arn <value> \
    --tag-key-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource (must be a `backup` ARN) |
| `--tag-key-list` | **Yes** | list | -- | List of tag keys to remove |

**Example:**
```bash
aws backup untag-resource \
    --resource-arn arn:aws:backup:us-east-1:123456789012:backup-plan:my-plan-id \
    --tag-key-list Environment CostCenter
```

**Output:** None

---

### 13.3 `list-tags`

Lists tags assigned to a Backup resource. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-tags \
    --resource-arn <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max items (1-1000) |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Tags": {
        "string": "string"
    }
}
```
