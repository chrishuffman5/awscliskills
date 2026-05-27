# Billing Groups

## 15.1 `create-billing-group`

Creates a billing group for cost allocation tagging.

**Synopsis:**
```bash
aws iot create-billing-group \
    --billing-group-name <value> \
    [--billing-group-properties <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--billing-group-name` | **Yes** | string | -- | Billing group name (1-128 chars) |
| `--billing-group-properties` | No | structure | None | `{billingGroupDescription: "string"}` |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "billingGroupName": "string",
    "billingGroupArn": "string",
    "billingGroupId": "string"
}
```

---

## 15.2 `describe-billing-group`

Describes a billing group.

**Synopsis:**
```bash
aws iot describe-billing-group \
    --billing-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--billing-group-name` | **Yes** | string | -- | Billing group name |

**Output Schema:**
```json
{
    "billingGroupName": "string",
    "billingGroupId": "string",
    "billingGroupArn": "string",
    "version": "long",
    "billingGroupProperties": {
        "billingGroupDescription": "string"
    },
    "billingGroupMetadata": {
        "creationDate": "timestamp"
    }
}
```

---

## 15.3 `list-billing-groups`

Lists billing groups. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-billing-groups \
    [--next-token <value>] \
    [--max-results <value>] \
    [--name-prefix-filter <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |
| `--name-prefix-filter` | No | string | None | Filter by name prefix |

**Output Schema:**
```json
{
    "billingGroups": [
        {
            "groupName": "string",
            "groupArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 15.4 `update-billing-group`

Updates a billing group.

**Synopsis:**
```bash
aws iot update-billing-group \
    --billing-group-name <value> \
    --billing-group-properties <value> \
    [--expected-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--billing-group-name` | **Yes** | string | -- | Billing group name |
| `--billing-group-properties` | **Yes** | structure | -- | Updated properties |
| `--expected-version` | No | long | None | Expected version for optimistic locking |

**Output Schema:**
```json
{
    "version": "long"
}
```

---

## 15.5 `delete-billing-group`

Deletes a billing group.

**Synopsis:**
```bash
aws iot delete-billing-group \
    --billing-group-name <value> \
    [--expected-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--billing-group-name` | **Yes** | string | -- | Billing group name |
| `--expected-version` | No | long | None | Expected version |

**Output:** None

---

## 15.6 `add-thing-to-billing-group`

Adds a thing to a billing group.

**Synopsis:**
```bash
aws iot add-thing-to-billing-group \
    [--billing-group-name <value>] \
    [--billing-group-arn <value>] \
    [--thing-name <value>] \
    [--thing-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--billing-group-name` | No | string | None | Billing group name (or use ARN) |
| `--billing-group-arn` | No | string | None | Billing group ARN |
| `--thing-name` | No | string | None | Thing name (or use ARN) |
| `--thing-arn` | No | string | None | Thing ARN |

**Output:** None

---

## 15.7 `remove-thing-from-billing-group`

Removes a thing from a billing group.

**Synopsis:**
```bash
aws iot remove-thing-from-billing-group \
    [--billing-group-name <value>] \
    [--billing-group-arn <value>] \
    [--thing-name <value>] \
    [--thing-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--billing-group-name` | No | string | None | Billing group name |
| `--billing-group-arn` | No | string | None | Billing group ARN |
| `--thing-name` | No | string | None | Thing name |
| `--thing-arn` | No | string | None | Thing ARN |

**Output:** None

---

## 15.8 `list-things-in-billing-group`

Lists things in a billing group. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-things-in-billing-group \
    --billing-group-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--billing-group-name` | **Yes** | string | -- | Billing group name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "things": ["string"],
    "nextToken": "string"
}
```
