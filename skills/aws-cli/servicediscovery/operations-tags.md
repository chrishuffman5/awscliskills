# Operations & Tags

### 4.1 `get-operation`

Gets the status of an asynchronous operation. Namespace creation, instance registration, and deregistration are asynchronous.

**Synopsis:**
```bash
aws servicediscovery get-operation \
    --operation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--operation-id` | **Yes** | string | -- | The operation ID returned by the async command (max 255 chars) |

**Output Schema:**
```json
{
    "Operation": {
        "Id": "string",
        "Type": "CREATE_NAMESPACE|DELETE_NAMESPACE|UPDATE_NAMESPACE|UPDATE_SERVICE|REGISTER_INSTANCE|DEREGISTER_INSTANCE",
        "Status": "SUBMITTED|PENDING|SUCCESS|FAIL",
        "ErrorMessage": "string",
        "ErrorCode": "string",
        "CreateDate": "timestamp",
        "UpdateDate": "timestamp",
        "Targets": {"string": "string"}
    }
}
```

---

### 4.2 `list-operations`

Lists operations that match the specified criteria. **Paginated.**

**Synopsis:**
```bash
aws servicediscovery list-operations \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filter by `NAMESPACE_ID`, `SERVICE_ID`, `STATUS`, `TYPE`, or `UPDATE_DATE`. Shorthand: `Name=string,Values=string,string,Condition=EQ\|IN\|BETWEEN\|BEGINS_WITH` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Operations": [
        {
            "Id": "string",
            "Status": "SUBMITTED|PENDING|SUCCESS|FAIL"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.3 `tag-resource`

Adds tags to a Cloud Map resource.

**Synopsis:**
```bash
aws servicediscovery tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource (max 1011 chars) |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string ...` (max 200 tags, key: 1-128 chars, value: 0-256 chars) |

**Output Schema:**

No output on success.

---

### 4.4 `untag-resource`

Removes tags from a Cloud Map resource.

**Synopsis:**
```bash
aws servicediscovery untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource (max 1011 chars) |
| `--tag-keys` | **Yes** | list(string) | -- | The tag keys to remove |

**Output Schema:**

No output on success.

---

### 4.5 `list-tags-for-resource`

Lists the tags for a Cloud Map resource.

**Synopsis:**
```bash
aws servicediscovery list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | The ARN of the resource (max 1011 chars) |

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
