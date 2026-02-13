# Serverless Lifecycle

### 13.1 `create-lifecycle-policy`

Creates a lifecycle policy for OpenSearch Serverless indexes. Controls index retention and data tiering.

**Synopsis:**
```bash
aws opensearchserverless create-lifecycle-policy \
    --type <value> \
    --name <value> \
    --policy <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Policy type: `retention` |
| `--name` | **Yes** | string | -- | Policy name (3-32 chars, pattern: `[a-z][a-z0-9-]+`) |
| `--policy` | **Yes** | string | -- | JSON lifecycle policy document (max 20480 chars) |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--client-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "lifecyclePolicyDetail": {
        "type": "retention",
        "name": "string",
        "policyVersion": "string",
        "description": "string",
        "policy": {},
        "createdDate": "long",
        "lastModifiedDate": "long"
    }
}
```

---

### 13.2 `delete-lifecycle-policy`

Deletes a lifecycle policy.

**Synopsis:**
```bash
aws opensearchserverless delete-lifecycle-policy \
    --type <value> \
    --name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Policy type: `retention` |
| `--name` | **Yes** | string | -- | Policy name |

**Output:** None

---

### 13.3 `batch-get-lifecycle-policy`

Returns details about one or more lifecycle policies.

**Synopsis:**
```bash
aws opensearchserverless batch-get-lifecycle-policy \
    --identifiers <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifiers` | **Yes** | list | -- | Policy identifiers. Shorthand: `type=retention,name=string ...` |

**Output Schema:**
```json
{
    "lifecyclePolicyDetails": [
        {
            "type": "retention",
            "name": "string",
            "policyVersion": "string",
            "description": "string",
            "policy": {},
            "createdDate": "long",
            "lastModifiedDate": "long"
        }
    ],
    "lifecyclePolicyErrorDetails": [
        {
            "type": "string",
            "name": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 13.4 `batch-get-effective-lifecycle-policy`

Returns the effective lifecycle policy for specific resources.

**Synopsis:**
```bash
aws opensearchserverless batch-get-effective-lifecycle-policy \
    --resource-identifiers <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-identifiers` | **Yes** | list | -- | Resource identifiers. Shorthand: `type=retention,resource=string ...` |

**Output Schema:**
```json
{
    "effectiveLifecyclePolicyDetails": [
        {
            "type": "retention",
            "resource": "string",
            "resourceType": "index",
            "policyName": "string",
            "noMinRetentionPeriod": "boolean",
            "retentionPeriod": "string"
        }
    ],
    "effectiveLifecyclePolicyErrorDetails": []
}
```

---

### 13.5 `list-lifecycle-policies`

Lists lifecycle policies. **Paginated operation.**

**Synopsis:**
```bash
aws opensearchserverless list-lifecycle-policies \
    --type <value> \
    [--resources <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Policy type: `retention` |
| `--resources` | No | list(string) | None | Filter by resource patterns |

**Output Schema:**
```json
{
    "lifecyclePolicySummaries": [
        {
            "type": "retention",
            "name": "string",
            "policyVersion": "string",
            "description": "string",
            "createdDate": "long",
            "lastModifiedDate": "long"
        }
    ],
    "nextToken": "string"
}
```

---

### 13.6 `update-lifecycle-policy`

Updates a lifecycle policy.

**Synopsis:**
```bash
aws opensearchserverless update-lifecycle-policy \
    --type <value> \
    --name <value> \
    --policy-version <value> \
    [--policy <value>] \
    [--description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Policy type: `retention` |
| `--name` | **Yes** | string | -- | Policy name |
| `--policy-version` | **Yes** | string | -- | Current policy version (for optimistic locking) |
| `--policy` | No | string | None | Updated policy document |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "lifecyclePolicyDetail": {
        "type": "retention",
        "name": "string",
        "policyVersion": "string",
        "policy": {},
        "lastModifiedDate": "long"
    }
}
```
