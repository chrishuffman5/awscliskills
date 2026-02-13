# Policies

### 2.1 `create-policy`

Creates a Cedar authorization policy in a policy store. Can be a static policy or a template-linked policy.

**Synopsis:**
```bash
aws verifiedpermissions create-policy \
    --policy-store-id <value> \
    --definition <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID (1-200 chars) |
| `--definition` | **Yes** | tagged union | -- | Policy definition: `static` or `templateLinked` |
| `--client-token` | No | string | Auto-generated | Idempotency token (1-64 chars) |

**Definition Structure (static):**
```json
{
    "static": {
        "description": "string",
        "statement": "string"
    }
}
```

**Definition Structure (templateLinked):**
```json
{
    "templateLinked": {
        "policyTemplateId": "string",
        "principal": {
            "entityType": "string",
            "entityId": "string"
        },
        "resource": {
            "entityType": "string",
            "entityId": "string"
        }
    }
}
```

**Output Schema:**
```json
{
    "policyStoreId": "string",
    "policyId": "string",
    "policyType": "STATIC|TEMPLATE_LINKED",
    "principal": {
        "entityType": "string",
        "entityId": "string"
    },
    "resource": {
        "entityType": "string",
        "entityId": "string"
    },
    "actions": [
        {
            "actionType": "string",
            "actionId": "string"
        }
    ],
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp",
    "effect": "Permit|Forbid"
}
```

---

### 2.2 `delete-policy`

Deletes the specified policy from a policy store.

**Synopsis:**
```bash
aws verifiedpermissions delete-policy \
    --policy-store-id <value> \
    --policy-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--policy-id` | **Yes** | string | -- | ID of the policy to delete |

**Output Schema:**

No output fields (empty response on success).

---

### 2.3 `get-policy`

Retrieves details about the specified policy.

**Synopsis:**
```bash
aws verifiedpermissions get-policy \
    --policy-store-id <value> \
    --policy-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--policy-id` | **Yes** | string | -- | ID of the policy to retrieve |

**Output Schema:**
```json
{
    "policyStoreId": "string",
    "policyId": "string",
    "policyType": "STATIC|TEMPLATE_LINKED",
    "principal": {
        "entityType": "string",
        "entityId": "string"
    },
    "resource": {
        "entityType": "string",
        "entityId": "string"
    },
    "actions": [
        {
            "actionType": "string",
            "actionId": "string"
        }
    ],
    "definition": {
        "static": {
            "description": "string",
            "statement": "string"
        },
        "templateLinked": {
            "policyTemplateId": "string",
            "principal": {
                "entityType": "string",
                "entityId": "string"
            },
            "resource": {
                "entityType": "string",
                "entityId": "string"
            }
        }
    },
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp",
    "effect": "Permit|Forbid"
}
```

---

### 2.4 `list-policies`

Lists policies in the specified policy store. **Paginated operation.**

**Synopsis:**
```bash
aws verifiedpermissions list-policies \
    --policy-store-id <value> \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--filter` | No | structure | None | Filter by policy type, principal, resource, or template |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
{
    "principal": {
        "unspecified": true,
        "identifier": {
            "entityType": "string",
            "entityId": "string"
        }
    },
    "resource": {
        "unspecified": true,
        "identifier": {
            "entityType": "string",
            "entityId": "string"
        }
    },
    "policyType": "STATIC|TEMPLATE_LINKED",
    "policyTemplateId": "string"
}
```

**Output Schema:**
```json
{
    "policies": [
        {
            "policyStoreId": "string",
            "policyId": "string",
            "policyType": "STATIC|TEMPLATE_LINKED",
            "principal": {
                "entityType": "string",
                "entityId": "string"
            },
            "resource": {
                "entityType": "string",
                "entityId": "string"
            },
            "actions": [
                {
                    "actionType": "string",
                    "actionId": "string"
                }
            ],
            "definition": {
                "static": {
                    "description": "string"
                },
                "templateLinked": {
                    "policyTemplateId": "string",
                    "principal": {
                        "entityType": "string",
                        "entityId": "string"
                    },
                    "resource": {
                        "entityType": "string",
                        "entityId": "string"
                    }
                }
            },
            "createdDate": "timestamp",
            "lastUpdatedDate": "timestamp",
            "effect": "Permit|Forbid"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.5 `update-policy`

Updates the specified policy. Only static policies can be updated; template-linked policies are updated by modifying the template.

**Synopsis:**
```bash
aws verifiedpermissions update-policy \
    --policy-store-id <value> \
    --policy-id <value> \
    --definition <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--policy-id` | **Yes** | string | -- | ID of the policy to update |
| `--definition` | **Yes** | tagged union | -- | Updated policy definition (static only) |

**Output Schema:**
```json
{
    "policyStoreId": "string",
    "policyId": "string",
    "policyType": "STATIC|TEMPLATE_LINKED",
    "principal": {
        "entityType": "string",
        "entityId": "string"
    },
    "resource": {
        "entityType": "string",
        "entityId": "string"
    },
    "actions": [
        {
            "actionType": "string",
            "actionId": "string"
        }
    ],
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp",
    "effect": "Permit|Forbid"
}
```

---

### 2.6 `batch-get-policy`

Retrieves information about multiple policies in a single request.

**Synopsis:**
```bash
aws verifiedpermissions batch-get-policy \
    --requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--requests` | **Yes** | list | -- | List of policy store ID + policy ID pairs to retrieve |

**Request Structure:**
```json
[
    {
        "policyStoreId": "string",
        "policyId": "string"
    }
]
```

**Output Schema:**
```json
{
    "results": [
        {
            "policyStoreId": "string",
            "policyId": "string",
            "policyType": "STATIC|TEMPLATE_LINKED",
            "definition": {
                "static": {
                    "description": "string",
                    "statement": "string"
                },
                "templateLinked": {
                    "policyTemplateId": "string",
                    "principal": {
                        "entityType": "string",
                        "entityId": "string"
                    },
                    "resource": {
                        "entityType": "string",
                        "entityId": "string"
                    }
                }
            },
            "createdDate": "timestamp",
            "lastUpdatedDate": "timestamp",
            "effect": "Permit|Forbid"
        }
    ],
    "errors": [
        {
            "code": "string",
            "policyStoreId": "string",
            "policyId": "string",
            "message": "string"
        }
    ]
}
```
