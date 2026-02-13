# Organizations & Tags

### 4.1 `tag-resource`

Adds tags to a RAM resource share or permission.

**Synopsis:**
```bash
aws ram tag-resource \
    --resource-share-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-arn` | **Yes** | string | -- | ARN of the resource share or permission to tag |
| `--tags` | **Yes** | list(structure) | -- | Tags to add. Structure: `key=string,value=string` |

**Output Schema:**

No output on success (HTTP 200).

---

### 4.2 `untag-resource`

Removes tags from a RAM resource share or permission.

**Synopsis:**
```bash
aws ram untag-resource \
    --resource-share-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-share-arn` | **Yes** | string | -- | ARN of the resource share or permission to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**

No output on success (HTTP 200).

---

### 4.3 `list-source-associations`

Lists source associations for a resource share. **Paginated operation.**

**Synopsis:**
```bash
aws ram list-source-associations \
    --association-type <value> \
    [--resource-share-arn <value>] \
    [--source <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-type` | **Yes** | string | -- | Association type filter |
| `--resource-share-arn` | No | string | None | Filter by resource share ARN |
| `--source` | No | string | None | Filter by source |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "sourceAssociations": [
        {
            "associationType": "string",
            "resourceShareArn": "string",
            "source": "string",
            "status": "string",
            "statusMessage": "string"
        }
    ],
    "nextToken": "string"
}
```
