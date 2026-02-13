# Attributes

### 11.1 `put-attributes`

Creates or updates attributes on an ECS resource (currently only container instances).

**Synopsis:**
```bash
aws ecs put-attributes \
    --attributes <value> \
    [--cluster <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attributes` | **Yes** | list | -- | Attributes to apply. Shorthand: `name=string,value=string,targetType=container-instance,targetId=string ...` |
| `--cluster` | No | string | `default` | Cluster short name or ARN |

**Attribute Structure:**
```json
{
    "name": "string",
    "value": "string",
    "targetType": "container-instance",
    "targetId": "string"
}
```

**Output Schema:**
```json
{
    "attributes": [
        {
            "name": "string",
            "value": "string",
            "targetType": "container-instance",
            "targetId": "string"
        }
    ]
}
```

---

### 11.2 `delete-attributes`

Deletes one or more custom attributes from an ECS resource.

**Synopsis:**
```bash
aws ecs delete-attributes \
    --attributes <value> \
    [--cluster <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attributes` | **Yes** | list | -- | Attributes to delete. Shorthand: `name=string,targetType=container-instance,targetId=string ...` |
| `--cluster` | No | string | `default` | Cluster short name or ARN |

**Output Schema:**
```json
{
    "attributes": [
        {
            "name": "string",
            "value": "string",
            "targetType": "container-instance",
            "targetId": "string"
        }
    ]
}
```

---

### 11.3 `list-attributes`

Lists the attributes for ECS resources within a specified target type and cluster.

**Synopsis:**
```bash
aws ecs list-attributes \
    --target-type <value> \
    [--cluster <value>] \
    [--attribute-name <value>] \
    [--attribute-value <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-type` | **Yes** | string | -- | `container-instance` |
| `--cluster` | No | string | `default` | Cluster short name or ARN |
| `--attribute-name` | No | string | None | Filter by attribute name |
| `--attribute-value` | No | string | None | Filter by attribute value (requires `--attribute-name`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "attributes": [
        {
            "name": "string",
            "value": "string",
            "targetType": "container-instance",
            "targetId": "string"
        }
    ],
    "nextToken": "string"
}
```
