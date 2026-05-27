# Authorization & Tags

### 5.1 `is-authorized`

Makes an authorization decision about a service request. Returns ALLOW or DENY based on Cedar policies in the policy store.

**Synopsis:**
```bash
aws verifiedpermissions is-authorized \
    --policy-store-id <value> \
    [--principal <value>] \
    [--action <value>] \
    [--resource <value>] \
    [--context <value>] \
    [--entities <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID (1-200 chars) |
| `--principal` | No | structure | None | The principal. Shorthand: `entityType=string,entityId=string` |
| `--action` | No | structure | None | The action. Shorthand: `actionType=string,actionId=string` |
| `--resource` | No | structure | None | The resource. Shorthand: `entityType=string,entityId=string` |
| `--context` | No | tagged union | None | Additional context: `contextMap` or `cedarJson` |
| `--entities` | No | tagged union | None | Additional entities: `entityList` or `cedarJson` |

**Output Schema:**
```json
{
    "decision": "ALLOW|DENY",
    "determiningPolicies": [
        {
            "policyId": "string"
        }
    ],
    "errors": [
        {
            "errorDescription": "string"
        }
    ]
}
```

---

### 5.2 `is-authorized-with-token`

Makes an authorization decision using an identity token (JWT) from a Cognito user pool or OIDC provider.

**Synopsis:**
```bash
aws verifiedpermissions is-authorized-with-token \
    --policy-store-id <value> \
    [--identity-token <value>] \
    [--access-token <value>] \
    [--action <value>] \
    [--resource <value>] \
    [--context <value>] \
    [--entities <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--identity-token` | No | string | None | OIDC identity token (1-131072 chars) |
| `--access-token` | No | string | None | OIDC access token (1-131072 chars) |
| `--action` | No | structure | None | The action. Shorthand: `actionType=string,actionId=string` |
| `--resource` | No | structure | None | The resource. Shorthand: `entityType=string,entityId=string` |
| `--context` | No | tagged union | None | Additional context |
| `--entities` | No | tagged union | None | Additional entities |

**Output Schema:**
```json
{
    "decision": "ALLOW|DENY",
    "determiningPolicies": [
        {
            "policyId": "string"
        }
    ],
    "errors": [
        {
            "errorDescription": "string"
        }
    ],
    "principal": {
        "entityType": "string",
        "entityId": "string"
    }
}
```

---

### 5.3 `batch-is-authorized`

Makes multiple authorization decisions in a single request (up to 30 requests per batch).

**Synopsis:**
```bash
aws verifiedpermissions batch-is-authorized \
    --policy-store-id <value> \
    --requests <value> \
    [--entities <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--requests` | **Yes** | list | -- | Array of up to 30 authorization requests |
| `--entities` | No | tagged union | None | Shared entities for all requests (max 100 principals, 100 resources) |

**Request Structure:**
```json
[
    {
        "principal": {
            "entityType": "string",
            "entityId": "string"
        },
        "action": {
            "actionType": "string",
            "actionId": "string"
        },
        "resource": {
            "entityType": "string",
            "entityId": "string"
        },
        "context": {
            "contextMap": {},
            "cedarJson": "string"
        }
    }
]
```

**Output Schema:**
```json
{
    "results": [
        {
            "request": {
                "principal": {
                    "entityType": "string",
                    "entityId": "string"
                },
                "action": {
                    "actionType": "string",
                    "actionId": "string"
                },
                "resource": {
                    "entityType": "string",
                    "entityId": "string"
                },
                "context": {}
            },
            "decision": "ALLOW|DENY",
            "determiningPolicies": [
                {
                    "policyId": "string"
                }
            ],
            "errors": [
                {
                    "errorDescription": "string"
                }
            ]
        }
    ]
}
```

---

### 5.4 `batch-is-authorized-with-token`

Makes multiple authorization decisions using identity tokens in a single request.

**Synopsis:**
```bash
aws verifiedpermissions batch-is-authorized-with-token \
    --policy-store-id <value> \
    --requests <value> \
    [--identity-token <value>] \
    [--access-token <value>] \
    [--entities <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--requests` | **Yes** | list | -- | Array of authorization requests |
| `--identity-token` | No | string | None | OIDC identity token |
| `--access-token` | No | string | None | OIDC access token |
| `--entities` | No | tagged union | None | Additional entities |

**Output Schema:**
```json
{
    "results": [
        {
            "request": {
                "action": {
                    "actionType": "string",
                    "actionId": "string"
                },
                "resource": {
                    "entityType": "string",
                    "entityId": "string"
                },
                "context": {}
            },
            "decision": "ALLOW|DENY",
            "determiningPolicies": [
                {
                    "policyId": "string"
                }
            ],
            "errors": [
                {
                    "errorDescription": "string"
                }
            ]
        }
    ],
    "principal": {
        "entityType": "string",
        "entityId": "string"
    }
}
```

---

### 5.5 `get-schema`

Retrieves the Cedar schema for the specified policy store.

**Synopsis:**
```bash
aws verifiedpermissions get-schema \
    --policy-store-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |

**Output Schema:**
```json
{
    "policyStoreId": "string",
    "schema": "string",
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp",
    "namespaces": ["string"]
}
```

---

### 5.6 `put-schema`

Creates or updates the Cedar schema for the specified policy store.

**Synopsis:**
```bash
aws verifiedpermissions put-schema \
    --policy-store-id <value> \
    --definition <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-store-id` | **Yes** | string | -- | Policy store ID |
| `--definition` | **Yes** | tagged union | -- | Schema definition as `cedarJson` string |

**Output Schema:**
```json
{
    "policyStoreId": "string",
    "namespaces": ["string"],
    "createdDate": "timestamp",
    "lastUpdatedDate": "timestamp"
}
```

---

### 5.7 `tag-resource`

Adds tags to the specified Verified Permissions resource.

**Synopsis:**
```bash
aws verifiedpermissions tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | map | -- | Key-value pairs to add (max 200 tags) |

**Output Schema:**

No output fields (empty response on success).

---

### 5.8 `untag-resource`

Removes tags from the specified Verified Permissions resource.

**Synopsis:**
```bash
aws verifiedpermissions untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to untag |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**

No output fields (empty response on success).

---

### 5.9 `list-tags-for-resource`

Lists tags attached to the specified Verified Permissions resource.

**Synopsis:**
```bash
aws verifiedpermissions list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```
