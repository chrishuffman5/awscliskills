# Things

## 1.1 `create-thing`

Creates a thing in the IoT registry.

**Synopsis:**
```bash
aws iot create-thing \
    --thing-name <value> \
    [--thing-type-name <value>] \
    [--attribute-payload <value>] \
    [--billing-group-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name (1-128 chars, pattern `[a-zA-Z0-9:_-]+`) |
| `--thing-type-name` | No | string | None | Associated thing type name |
| `--attribute-payload` | No | structure | None | Attributes (up to 3 key-value pairs). `{attributes:{},merge:boolean}` |
| `--billing-group-name` | No | string | None | Billing group to add the thing to |

**Output Schema:**
```json
{
    "thingName": "string",
    "thingArn": "string",
    "thingId": "string"
}
```

---

## 1.2 `describe-thing`

Describes a thing including attributes and connectivity.

**Synopsis:**
```bash
aws iot describe-thing \
    --thing-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Name of the thing |

**Output Schema:**
```json
{
    "defaultClientId": "string",
    "thingName": "string",
    "thingId": "string",
    "thingArn": "string",
    "thingTypeName": "string",
    "attributes": {"string": "string"},
    "version": "long",
    "billingGroupName": "string"
}
```

---

## 1.3 `list-things`

Lists things in the registry. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-things \
    [--next-token <value>] \
    [--max-results <value>] \
    [--attribute-name <value>] \
    [--attribute-value <value>] \
    [--thing-type-name <value>] \
    [--use-prefix-attribute-value | --no-use-prefix-attribute-value] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |
| `--attribute-name` | No | string | None | Filter by attribute name |
| `--attribute-value` | No | string | None | Filter by attribute value |
| `--thing-type-name` | No | string | None | Filter by thing type |
| `--use-prefix-attribute-value` | No | boolean | false | Use prefix matching for attribute value |

**Output Schema:**
```json
{
    "things": [
        {
            "thingName": "string",
            "thingTypeName": "string",
            "thingArn": "string",
            "attributes": {"string": "string"},
            "version": "long"
        }
    ],
    "nextToken": "string"
}
```

---

## 1.4 `update-thing`

Updates a thing's attributes or type.

**Synopsis:**
```bash
aws iot update-thing \
    --thing-name <value> \
    [--thing-type-name <value>] \
    [--attribute-payload <value>] \
    [--expected-version <value>] \
    [--remove-thing-type | --no-remove-thing-type] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Name of the thing to update |
| `--thing-type-name` | No | string | None | New thing type |
| `--attribute-payload` | No | structure | None | Updated attributes |
| `--expected-version` | No | long | None | Expected version for optimistic locking |
| `--remove-thing-type` | No | boolean | false | Remove thing type association |

**Output:** None

---

## 1.5 `delete-thing`

Deletes a thing from the registry.

**Synopsis:**
```bash
aws iot delete-thing \
    --thing-name <value> \
    [--expected-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Name of the thing to delete |
| `--expected-version` | No | long | None | Expected version for optimistic locking |

**Output:** None

---

## 1.6 `create-thing-type`

Creates a thing type with searchable attributes.

**Synopsis:**
```bash
aws iot create-thing-type \
    --thing-type-name <value> \
    [--thing-type-properties <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-type-name` | **Yes** | string | -- | Thing type name (1-128 chars) |
| `--thing-type-properties` | No | structure | None | Properties: `thingTypeDescription`, `searchableAttributes` (up to 3) |
| `--tags` | No | list | None | Tags |

**ThingTypeProperties:**
```json
{
    "thingTypeDescription": "string",
    "searchableAttributes": ["string"]
}
```

**Output Schema:**
```json
{
    "thingTypeName": "string",
    "thingTypeArn": "string",
    "thingTypeId": "string"
}
```

---

## 1.7 `describe-thing-type`

Describes a thing type.

**Synopsis:**
```bash
aws iot describe-thing-type \
    --thing-type-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-type-name` | **Yes** | string | -- | Name of the thing type |

**Output Schema:**
```json
{
    "thingTypeName": "string",
    "thingTypeId": "string",
    "thingTypeArn": "string",
    "thingTypeProperties": {
        "thingTypeDescription": "string",
        "searchableAttributes": ["string"]
    },
    "thingTypeMetadata": {
        "deprecated": "boolean",
        "deprecationDate": "timestamp",
        "creationDate": "timestamp"
    }
}
```

---

## 1.8 `list-thing-types`

Lists thing types. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-thing-types \
    [--next-token <value>] \
    [--max-results <value>] \
    [--thing-type-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |
| `--thing-type-name` | No | string | None | Filter by name prefix |

**Output Schema:**
```json
{
    "thingTypes": [
        {
            "thingTypeName": "string",
            "thingTypeArn": "string",
            "thingTypeProperties": {},
            "thingTypeMetadata": {}
        }
    ],
    "nextToken": "string"
}
```

---

## 1.9 `update-thing-type`

Updates a thing type description.

**Synopsis:**
```bash
aws iot update-thing-type \
    --thing-type-name <value> \
    [--thing-type-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-type-name` | **Yes** | string | -- | Name of the thing type |
| `--thing-type-properties` | No | structure | None | Updated properties |

**Output:** None

---

## 1.10 `delete-thing-type`

Deletes a thing type. Must be deprecated first.

**Synopsis:**
```bash
aws iot delete-thing-type \
    --thing-type-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-type-name` | **Yes** | string | -- | Name of the thing type |

**Output:** None

---

## 1.11 `deprecate-thing-type`

Deprecates a thing type (5-minute wait before deletion).

**Synopsis:**
```bash
aws iot deprecate-thing-type \
    --thing-type-name <value> \
    [--undo-deprecate | --no-undo-deprecate] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-type-name` | **Yes** | string | -- | Name of the thing type |
| `--undo-deprecate` | No | boolean | false | Undo the deprecation |

**Output:** None

---

## 1.12 `create-thing-group`

Creates a static thing group.

**Synopsis:**
```bash
aws iot create-thing-group \
    --thing-group-name <value> \
    [--parent-group-name <value>] \
    [--thing-group-properties <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-group-name` | **Yes** | string | -- | Thing group name (1-128 chars) |
| `--parent-group-name` | No | string | None | Parent group for hierarchy |
| `--thing-group-properties` | No | structure | None | `thingGroupDescription`, `attributePayload` |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "thingGroupName": "string",
    "thingGroupArn": "string",
    "thingGroupId": "string"
}
```

---

## 1.13 `describe-thing-group`

Describes a thing group.

**Synopsis:**
```bash
aws iot describe-thing-group \
    --thing-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-group-name` | **Yes** | string | -- | Name of the thing group |

**Output Schema:**
```json
{
    "thingGroupName": "string",
    "thingGroupId": "string",
    "thingGroupArn": "string",
    "version": "long",
    "thingGroupProperties": {
        "thingGroupDescription": "string",
        "attributePayload": {"attributes": {}, "merge": "boolean"}
    },
    "thingGroupMetadata": {
        "parentGroupName": "string",
        "rootToParentThingGroups": [{"groupName": "string", "groupArn": "string"}],
        "creationDate": "timestamp"
    },
    "indexName": "string",
    "queryString": "string",
    "queryVersion": "string",
    "status": "ACTIVE|BUILDING|REBUILDING"
}
```

---

## 1.14 `list-thing-groups`

Lists thing groups. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-thing-groups \
    [--next-token <value>] \
    [--max-results <value>] \
    [--parent-group <value>] \
    [--name-prefix-filter <value>] \
    [--recursive | --no-recursive] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |
| `--parent-group` | No | string | None | Filter by parent group |
| `--name-prefix-filter` | No | string | None | Filter by name prefix |
| `--recursive` | No | boolean | false | Include child groups recursively |

**Output Schema:**
```json
{
    "thingGroups": [
        {
            "groupName": "string",
            "groupArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 1.15 `update-thing-group`

Updates a thing group's properties.

**Synopsis:**
```bash
aws iot update-thing-group \
    --thing-group-name <value> \
    --thing-group-properties <value> \
    [--expected-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-group-name` | **Yes** | string | -- | Name of the thing group |
| `--thing-group-properties` | **Yes** | structure | -- | Updated properties |
| `--expected-version` | No | long | None | Expected version for optimistic locking |

**Output Schema:**
```json
{
    "version": "long"
}
```

---

## 1.16 `delete-thing-group`

Deletes a thing group.

**Synopsis:**
```bash
aws iot delete-thing-group \
    --thing-group-name <value> \
    [--expected-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-group-name` | **Yes** | string | -- | Name of the thing group |
| `--expected-version` | No | long | None | Expected version for optimistic locking |

**Output:** None

---

## 1.17 `create-dynamic-thing-group`

Creates a dynamic thing group based on a fleet index query.

**Synopsis:**
```bash
aws iot create-dynamic-thing-group \
    --thing-group-name <value> \
    --query-string <value> \
    [--thing-group-properties <value>] \
    [--index-name <value>] \
    [--query-version <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-group-name` | **Yes** | string | -- | Dynamic thing group name (1-128 chars) |
| `--query-string` | **Yes** | string | -- | Fleet indexing query string |
| `--thing-group-properties` | No | structure | None | Group properties |
| `--index-name` | No | string | AWS_Things | Index to search |
| `--query-version` | No | string | None | Query version |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "thingGroupName": "string",
    "thingGroupArn": "string",
    "thingGroupId": "string",
    "indexName": "string",
    "queryString": "string",
    "queryVersion": "string"
}
```

---

## 1.18 `update-dynamic-thing-group`

Updates a dynamic thing group query.

**Synopsis:**
```bash
aws iot update-dynamic-thing-group \
    --thing-group-name <value> \
    [--thing-group-properties <value>] \
    [--expected-version <value>] \
    [--index-name <value>] \
    [--query-string <value>] \
    [--query-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-group-name` | **Yes** | string | -- | Name of the dynamic thing group |
| `--thing-group-properties` | No | structure | None | Updated properties |
| `--expected-version` | No | long | None | Expected version |
| `--index-name` | No | string | None | Index name |
| `--query-string` | No | string | None | Updated query |
| `--query-version` | No | string | None | Query version |

**Output Schema:**
```json
{
    "version": "long"
}
```

---

## 1.19 `delete-dynamic-thing-group`

Deletes a dynamic thing group.

**Synopsis:**
```bash
aws iot delete-dynamic-thing-group \
    --thing-group-name <value> \
    [--expected-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-group-name` | **Yes** | string | -- | Name of the dynamic thing group |
| `--expected-version` | No | long | None | Expected version |

**Output:** None

---

## 1.20 `add-thing-to-thing-group`

Adds a thing to a thing group.

**Synopsis:**
```bash
aws iot add-thing-to-thing-group \
    [--thing-group-name <value>] \
    [--thing-group-arn <value>] \
    [--thing-name <value>] \
    [--thing-arn <value>] \
    [--override-dynamic-groups | --no-override-dynamic-groups] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-group-name` | No | string | None | Thing group name (or use ARN) |
| `--thing-group-arn` | No | string | None | Thing group ARN |
| `--thing-name` | No | string | None | Thing name (or use ARN) |
| `--thing-arn` | No | string | None | Thing ARN |
| `--override-dynamic-groups` | No | boolean | false | Override dynamic group membership |

**Output:** None

---

## 1.21 `remove-thing-from-thing-group`

Removes a thing from a thing group.

**Synopsis:**
```bash
aws iot remove-thing-from-thing-group \
    [--thing-group-name <value>] \
    [--thing-group-arn <value>] \
    [--thing-name <value>] \
    [--thing-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-group-name` | No | string | None | Thing group name |
| `--thing-group-arn` | No | string | None | Thing group ARN |
| `--thing-name` | No | string | None | Thing name |
| `--thing-arn` | No | string | None | Thing ARN |

**Output:** None

---

## 1.22 `list-things-in-thing-group`

Lists things in a thing group. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-things-in-thing-group \
    --thing-group-name <value> \
    [--recursive | --no-recursive] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-group-name` | **Yes** | string | -- | Name of the thing group |
| `--recursive` | No | boolean | false | Include things in child groups |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "things": ["string"],
    "nextToken": "string"
}
```

---

## 1.23 `list-thing-groups-for-thing`

Lists thing groups that a thing belongs to. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-thing-groups-for-thing \
    --thing-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "thingGroups": [
        {
            "groupName": "string",
            "groupArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 1.24 `list-thing-principals`

Lists principals (certificates) associated with a thing.

**Synopsis:**
```bash
aws iot list-thing-principals \
    --thing-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "principals": ["string"],
    "nextToken": "string"
}
```

---

## 1.25 `list-thing-principals-v2`

Lists principals for a thing with additional details. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-thing-principals-v2 \
    --thing-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "thingPrincipalObjects": [
        {
            "principal": "string",
            "thingPrincipalType": "EXCLUSIVE_THING|NON_EXCLUSIVE_THING"
        }
    ],
    "nextToken": "string"
}
```

---

## 1.26 `list-principal-things`

Lists things attached to a principal (certificate ARN).

**Synopsis:**
```bash
aws iot list-principal-things \
    --principal <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--principal` | **Yes** | string | -- | Principal ARN (certificate or Cognito identity) |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "things": ["string"],
    "nextToken": "string"
}
```

---

## 1.27 `list-principal-things-v2`

Lists things attached to a principal with details.

**Synopsis:**
```bash
aws iot list-principal-things-v2 \
    --principal <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--thing-principal-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--principal` | **Yes** | string | -- | Principal ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |
| `--thing-principal-type` | No | string | None | Filter: `EXCLUSIVE_THING` or `NON_EXCLUSIVE_THING` |

**Output Schema:**
```json
{
    "thingPrincipalObjects": [
        {
            "thingName": "string",
            "thingPrincipalType": "EXCLUSIVE_THING|NON_EXCLUSIVE_THING"
        }
    ],
    "nextToken": "string"
}
```

---

## 1.28 `attach-thing-principal`

Attaches a certificate or other principal to a thing.

**Synopsis:**
```bash
aws iot attach-thing-principal \
    --thing-name <value> \
    --principal <value> \
    [--thing-principal-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--principal` | **Yes** | string | -- | Principal ARN (certificate ARN) |
| `--thing-principal-type` | No | string | None | `EXCLUSIVE_THING` or `NON_EXCLUSIVE_THING` |

**Output:** None

---

## 1.29 `detach-thing-principal`

Detaches a principal from a thing.

**Synopsis:**
```bash
aws iot detach-thing-principal \
    --thing-name <value> \
    --principal <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--principal` | **Yes** | string | -- | Principal ARN |

**Output:** None

---

## 1.30 `start-thing-registration-task`

Starts a bulk thing registration task from an S3 file.

**Synopsis:**
```bash
aws iot start-thing-registration-task \
    --template-body <value> \
    --input-file-bucket <value> \
    --input-file-key <value> \
    --role-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-body` | **Yes** | string | -- | Provisioning template body |
| `--input-file-bucket` | **Yes** | string | -- | S3 bucket with registration file |
| `--input-file-key` | **Yes** | string | -- | S3 key of registration file |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for S3 access |

**Output Schema:**
```json
{
    "taskId": "string"
}
```

---

## 1.31 `stop-thing-registration-task`

Stops a bulk thing registration task.

**Synopsis:**
```bash
aws iot stop-thing-registration-task \
    --task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Task ID |

**Output:** None

---

## 1.32 `describe-thing-registration-task`

Describes a bulk thing registration task.

**Synopsis:**
```bash
aws iot describe-thing-registration-task \
    --task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Task ID |

**Output Schema:**
```json
{
    "taskId": "string",
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp",
    "templateBody": "string",
    "inputFileBucket": "string",
    "inputFileKey": "string",
    "roleArn": "string",
    "status": "InProgress|Completed|Failed|Cancelled|Cancelling",
    "message": "string",
    "successCount": "integer",
    "failureCount": "integer",
    "percentageProgress": "integer"
}
```

---

## 1.33 `list-thing-registration-tasks`

Lists bulk thing registration tasks. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-thing-registration-tasks \
    [--next-token <value>] \
    [--max-results <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |
| `--status` | No | string | None | Filter: `InProgress`, `Completed`, `Failed`, `Cancelled`, `Cancelling` |

**Output Schema:**
```json
{
    "taskIds": ["string"],
    "nextToken": "string"
}
```

---

## 1.34 `list-thing-registration-task-reports`

Lists success/failure reports for a registration task.

**Synopsis:**
```bash
aws iot list-thing-registration-task-reports \
    --task-id <value> \
    --report-type <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Task ID |
| `--report-type` | **Yes** | string | -- | `ERRORS` or `RESULTS` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "resourceLinks": ["string"],
    "reportType": "ERRORS|RESULTS",
    "nextToken": "string"
}
```

---

## 1.35 `register-thing`

Registers a thing using a provisioning template.

**Synopsis:**
```bash
aws iot register-thing \
    --template-body <value> \
    [--parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-body` | **Yes** | string | -- | Provisioning template body |
| `--parameters` | No | map | None | Template parameters |

**Output Schema:**
```json
{
    "certificatePem": "string",
    "resourceArns": {"string": "string"}
}
```

---

## 1.36 `update-thing-groups-for-thing`

Updates thing group memberships for a thing.

**Synopsis:**
```bash
aws iot update-thing-groups-for-thing \
    [--thing-name <value>] \
    [--thing-groups-to-add <value>] \
    [--thing-groups-to-remove <value>] \
    [--override-dynamic-groups | --no-override-dynamic-groups] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | No | string | None | Thing name |
| `--thing-groups-to-add` | No | list | None | Groups to add the thing to |
| `--thing-groups-to-remove` | No | list | None | Groups to remove the thing from |
| `--override-dynamic-groups` | No | boolean | false | Override dynamic group membership |

**Output:** None

---

## 1.37 `get-thing-connectivity-data`

Gets connectivity data for a thing (when last connected/disconnected).

**Synopsis:**
```bash
aws iot get-thing-connectivity-data \
    --thing-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name |

**Output Schema:**
```json
{
    "thingName": "string",
    "connected": "boolean",
    "timestamp": "long",
    "disconnectReason": "string"
}
```
