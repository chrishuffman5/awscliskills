# Tagging

### 1.1 `get-resources`

Returns all tagged resources in the account/region that match the specified tag filters and resource type filters. **Paginated operation.**

**Synopsis:**
```bash
aws resourcegroupstaggingapi get-resources \
    [--tag-filters <value>] \
    [--resource-type-filters <value>] \
    [--tags-per-page <value>] \
    [--include-compliance-details | --no-include-compliance-details] \
    [--exclude-compliant-resources | --no-exclude-compliant-resources] \
    [--resource-arn-list <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tag-filters` | No | list | None | Filter by tag key/values. Shorthand: `Key=string,Values=string,string ...` |
| `--resource-type-filters` | No | list(string) | None | Filter by resource type (e.g., `ec2:instance`, `s3`). Up to 100 values |
| `--tags-per-page` | No | integer | 100 | Maximum number of tags returned per page (legacy parameter) |
| `--include-compliance-details` | No | boolean | false | Include compliance details in results |
| `--exclude-compliant-resources` | No | boolean | false | Only return noncompliant resources (requires `--include-compliance-details`) |
| `--resource-arn-list` | No | list(string) | None | Filter to specific resource ARNs. Up to 100 ARNs |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PaginationToken": "string",
    "ResourceTagMappingList": [
        {
            "ResourceARN": "string",
            "Tags": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ],
            "ComplianceDetails": {
                "NoncompliantKeys": ["string"],
                "KeysWithNoncompliantValues": ["string"],
                "ComplianceStatus": true|false
            }
        }
    ]
}
```

---

### 1.2 `get-tag-keys`

Returns all tag keys currently in use in the account/region. **Paginated operation.**

**Synopsis:**
```bash
aws resourcegroupstaggingapi get-tag-keys \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PaginationToken": "string",
    "TagKeys": ["string"]
}
```

---

### 1.3 `get-tag-values`

Returns all tag values for a specified tag key in the account/region. **Paginated operation.**

**Synopsis:**
```bash
aws resourcegroupstaggingapi get-tag-values \
    --key <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key` | **Yes** | string | -- | The tag key for which to retrieve values |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PaginationToken": "string",
    "TagValues": ["string"]
}
```

---

### 1.4 `tag-resources`

Applies one or more tags to the specified resources. Each resource can have a maximum of 50 user-created tags. Tags applied to one resource do not automatically propagate to related resources.

**Synopsis:**
```bash
aws resourcegroupstaggingapi tag-resources \
    --resource-arn-list <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn-list` | **Yes** | list(string) | -- | ARNs of resources to tag. Up to 20 ARNs |
| `--tags` | **Yes** | map | -- | Tags to apply. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "FailedResourcesMap": {
        "ResourceARN": {
            "StatusCode": "integer",
            "ErrorCode": "InternalServiceException|InvalidParameterException",
            "ErrorMessage": "string"
        }
    }
}
```

---

### 1.5 `untag-resources`

Removes the specified tags from the specified resources. When a tag key is specified, the action removes both the key and its associated value.

**Synopsis:**
```bash
aws resourcegroupstaggingapi untag-resources \
    --resource-arn-list <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn-list` | **Yes** | list(string) | -- | ARNs of resources to untag. Up to 20 ARNs |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove. Up to 50 tag keys |

**Output Schema:**
```json
{
    "FailedResourcesMap": {
        "ResourceARN": {
            "StatusCode": "integer",
            "ErrorCode": "InternalServiceException|InvalidParameterException",
            "ErrorMessage": "string"
        }
    }
}
```
