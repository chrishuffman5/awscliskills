# Protections

### 2.1 `create-protection`

Enables Shield Advanced protection for a specific AWS resource.

**Synopsis:**
```bash
aws shield create-protection \
    --name <value> \
    --resource-arn <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Friendly name for the protection (1-128 chars) |
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to protect |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` (max 200) |

**Output Schema:**
```json
{
    "ProtectionId": "string"
}
```

---

### 2.2 `delete-protection`

Deletes a Shield Advanced protection.

**Synopsis:**
```bash
aws shield delete-protection \
    --protection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protection-id` | **Yes** | string | -- | Protection ID to delete (UUID format) |

**Output Schema:** Empty on success.

---

### 2.3 `describe-protection`

Describes a Shield Advanced protection.

**Synopsis:**
```bash
aws shield describe-protection \
    [--protection-id <value>] \
    [--resource-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protection-id` | No | string | None | Protection ID (specify this or `--resource-arn`) |
| `--resource-arn` | No | string | None | Resource ARN (specify this or `--protection-id`) |

**Output Schema:**
```json
{
    "Protection": {
        "Id": "string",
        "Name": "string",
        "ResourceArn": "string",
        "HealthCheckIds": ["string"],
        "ProtectionArn": "string",
        "ApplicationLayerAutomaticResponseConfiguration": {
            "Status": "ENABLED|DISABLED",
            "Action": {
                "Block": {},
                "Count": {}
            }
        }
    }
}
```

---

### 2.4 `list-protections`

Lists all Shield Advanced protections. **Paginated.**

**Synopsis:**
```bash
aws shield list-protections \
    [--inclusion-filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inclusion-filters` | No | structure | None | Filter by resource ARNs, protection names, resource types |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Inclusion Filters Structure:**
```json
{
    "ResourceArns": ["string"],
    "ProtectionNames": ["string"],
    "ResourceTypes": ["CLOUDFRONT_DISTRIBUTION|ROUTE_53_HOSTED_ZONE|ELASTIC_IP_ALLOCATION|CLASSIC_LOAD_BALANCER|APPLICATION_LOAD_BALANCER|GLOBAL_ACCELERATOR"]
}
```

**Output Schema:**
```json
{
    "Protections": [
        {
            "Id": "string",
            "Name": "string",
            "ResourceArn": "string",
            "HealthCheckIds": ["string"],
            "ProtectionArn": "string",
            "ApplicationLayerAutomaticResponseConfiguration": {
                "Status": "ENABLED|DISABLED",
                "Action": {
                    "Block": {},
                    "Count": {}
                }
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `create-protection-group`

Creates a grouping of protected resources for collective detection and mitigation.

**Synopsis:**
```bash
aws shield create-protection-group \
    --protection-group-id <value> \
    --aggregation <value> \
    --pattern <value> \
    [--resource-type <value>] \
    [--members <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protection-group-id` | **Yes** | string | -- | Group ID (1-36 chars) |
| `--aggregation` | **Yes** | string | -- | Aggregation method: `SUM`, `MEAN`, `MAX` |
| `--pattern` | **Yes** | string | -- | Grouping pattern: `ALL`, `ARBITRARY`, `BY_RESOURCE_TYPE` |
| `--resource-type` | No | string | None | Resource type (required when pattern is `BY_RESOURCE_TYPE`) |
| `--members` | No | list(string) | None | Resource ARNs (required when pattern is `ARBITRARY`, max 10000) |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:** Empty on success.

---

### 2.6 `delete-protection-group`

Deletes a protection group.

**Synopsis:**
```bash
aws shield delete-protection-group \
    --protection-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protection-group-id` | **Yes** | string | -- | Group ID to delete |

**Output Schema:** Empty on success.

---

### 2.7 `describe-protection-group`

Returns the details of a protection group.

**Synopsis:**
```bash
aws shield describe-protection-group \
    --protection-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protection-group-id` | **Yes** | string | -- | Group ID |

**Output Schema:**
```json
{
    "ProtectionGroup": {
        "ProtectionGroupId": "string",
        "Aggregation": "SUM|MEAN|MAX",
        "Pattern": "ALL|ARBITRARY|BY_RESOURCE_TYPE",
        "ResourceType": "CLOUDFRONT_DISTRIBUTION|ROUTE_53_HOSTED_ZONE|ELASTIC_IP_ALLOCATION|CLASSIC_LOAD_BALANCER|APPLICATION_LOAD_BALANCER|GLOBAL_ACCELERATOR",
        "Members": ["string"],
        "ProtectionGroupArn": "string"
    }
}
```

---

### 2.8 `list-protection-groups`

Lists all protection groups. **Paginated.**

**Synopsis:**
```bash
aws shield list-protection-groups \
    [--inclusion-filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inclusion-filters` | No | structure | None | Filter by group IDs, patterns, resource types, aggregations |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ProtectionGroups": [
        {
            "ProtectionGroupId": "string",
            "Aggregation": "SUM|MEAN|MAX",
            "Pattern": "ALL|ARBITRARY|BY_RESOURCE_TYPE",
            "ResourceType": "string",
            "Members": ["string"],
            "ProtectionGroupArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.9 `update-protection-group`

Updates an existing protection group.

**Synopsis:**
```bash
aws shield update-protection-group \
    --protection-group-id <value> \
    --aggregation <value> \
    --pattern <value> \
    [--resource-type <value>] \
    [--members <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protection-group-id` | **Yes** | string | -- | Group ID to update |
| `--aggregation` | **Yes** | string | -- | Updated aggregation: `SUM`, `MEAN`, `MAX` |
| `--pattern` | **Yes** | string | -- | Updated pattern: `ALL`, `ARBITRARY`, `BY_RESOURCE_TYPE` |
| `--resource-type` | No | string | None | Updated resource type |
| `--members` | No | list(string) | None | Updated member ARNs |

**Output Schema:** Empty on success.

---

### 2.10 `list-resources-in-protection-group`

Returns the resource ARNs that are included in a protection group. **Paginated.**

**Synopsis:**
```bash
aws shield list-resources-in-protection-group \
    --protection-group-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protection-group-id` | **Yes** | string | -- | Protection group ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ResourceArns": ["string"],
    "NextToken": "string"
}
```
