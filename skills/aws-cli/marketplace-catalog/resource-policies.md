# Resource Policies

### 3.1 `get-resource-policy`

Gets a resource-based policy of an entity identified by its resource ARN.

**Synopsis:**
```bash
aws marketplace-catalog get-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the entity resource (max 255 chars) |

**Output Schema:**
```json
{
    "Policy": "string"
}
```

| Field | Description |
|-------|-------------|
| `Policy` | The policy document formatted as a JSON string (max 10240 chars) |

---

### 3.2 `put-resource-policy`

Attaches or updates a resource-based policy on an entity (e.g., `AmiProduct`, `ContainerProduct`).

**Synopsis:**
```bash
aws marketplace-catalog put-resource-policy \
    --resource-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the entity resource to attach the policy to (max 255 chars) |
| `--policy` | **Yes** | string | -- | The policy document in JSON format (max 10240 chars) |

**Output:** None

---

### 3.3 `delete-resource-policy`

Deletes a resource-based policy from an entity identified by its resource ARN.

**Synopsis:**
```bash
aws marketplace-catalog delete-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the entity resource to delete the policy from (max 255 chars) |

**Output:** None
