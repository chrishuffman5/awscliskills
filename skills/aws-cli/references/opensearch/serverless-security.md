# Serverless Security

### 11.1 `create-security-policy`

Creates a security policy (encryption or network) for OpenSearch Serverless.

**Synopsis:**
```bash
aws opensearchserverless create-security-policy \
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
| `--type` | **Yes** | string | -- | Policy type: `encryption` or `network` |
| `--name` | **Yes** | string | -- | Policy name (3-32 chars, pattern: `[a-z][a-z0-9-]+`) |
| `--policy` | **Yes** | string | -- | JSON policy document (max 20480 chars) |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--client-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "securityPolicyDetail": {
        "type": "encryption|network",
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

### 11.2 `delete-security-policy`

Deletes a security policy.

**Synopsis:**
```bash
aws opensearchserverless delete-security-policy \
    --type <value> \
    --name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Policy type: `encryption` or `network` |
| `--name` | **Yes** | string | -- | Policy name |

**Output:** None

---

### 11.3 `get-security-policy`

Returns details about a security policy.

**Synopsis:**
```bash
aws opensearchserverless get-security-policy \
    --type <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Policy type: `encryption` or `network` |
| `--name` | **Yes** | string | -- | Policy name |

**Output Schema:**
```json
{
    "securityPolicyDetail": {
        "type": "string",
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

### 11.4 `list-security-policies`

Lists security policies. **Paginated operation.**

**Synopsis:**
```bash
aws opensearchserverless list-security-policies \
    --type <value> \
    [--resource <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Policy type: `encryption` or `network` |
| `--resource` | No | list(string) | None | Filter by resource patterns |

**Output Schema:**
```json
{
    "securityPolicySummaries": [
        {
            "type": "string",
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

### 11.5 `update-security-policy`

Updates a security policy.

**Synopsis:**
```bash
aws opensearchserverless update-security-policy \
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
| `--type` | **Yes** | string | -- | Policy type: `encryption` or `network` |
| `--name` | **Yes** | string | -- | Policy name |
| `--policy-version` | **Yes** | string | -- | Current policy version (for optimistic locking) |
| `--policy` | No | string | None | Updated policy document |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "securityPolicyDetail": {
        "type": "string",
        "name": "string",
        "policyVersion": "string",
        "policy": {},
        "lastModifiedDate": "long"
    }
}
```

---

### 11.6 `create-access-policy`

Creates a data access policy for OpenSearch Serverless collections and indexes.

**Synopsis:**
```bash
aws opensearchserverless create-access-policy \
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
| `--type` | **Yes** | string | -- | Policy type: `data` |
| `--name` | **Yes** | string | -- | Policy name (3-32 chars) |
| `--policy` | **Yes** | string | -- | JSON access policy document |
| `--description` | No | string | None | Description |
| `--client-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "accessPolicyDetail": {
        "type": "data",
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

### 11.7 `delete-access-policy`

Deletes a data access policy.

**Synopsis:**
```bash
aws opensearchserverless delete-access-policy \
    --type <value> \
    --name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Policy type: `data` |
| `--name` | **Yes** | string | -- | Policy name |

**Output:** None

---

### 11.8 `get-access-policy`

Returns details about an access policy.

**Synopsis:**
```bash
aws opensearchserverless get-access-policy \
    --type <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Policy type: `data` |
| `--name` | **Yes** | string | -- | Policy name |

**Output Schema:**
```json
{
    "accessPolicyDetail": {
        "type": "data",
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

### 11.9 `list-access-policies`

Lists data access policies. **Paginated operation.**

**Synopsis:**
```bash
aws opensearchserverless list-access-policies \
    --type <value> \
    [--resource <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Policy type: `data` |
| `--resource` | No | list(string) | None | Filter by resource patterns |

**Output Schema:**
```json
{
    "accessPolicySummaries": [
        {
            "type": "data",
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

### 11.10 `update-access-policy`

Updates a data access policy.

**Synopsis:**
```bash
aws opensearchserverless update-access-policy \
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
| `--type` | **Yes** | string | -- | Policy type: `data` |
| `--name` | **Yes** | string | -- | Policy name |
| `--policy-version` | **Yes** | string | -- | Current policy version |
| `--policy` | No | string | None | Updated policy document |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "accessPolicyDetail": {
        "type": "data",
        "name": "string",
        "policyVersion": "string",
        "policy": {},
        "lastModifiedDate": "long"
    }
}
```

---

### 11.11 `create-security-config`

Creates a SAML or IAM Identity Center security configuration for OpenSearch Serverless.

**Synopsis:**
```bash
aws opensearchserverless create-security-config \
    --name <value> \
    --type <value> \
    [--description <value>] \
    [--saml-options <value>] \
    [--iam-identity-center-options <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Config name (3-32 chars) |
| `--type` | **Yes** | string | -- | `saml` or `iamidentitycenter` |
| `--description` | No | string | None | Description |
| `--saml-options` | No | structure | None | SAML provider config |
| `--iam-identity-center-options` | No | structure | None | IAM Identity Center config |

**Output Schema:**
```json
{
    "securityConfigDetail": {
        "id": "string",
        "type": "saml|iamidentitycenter",
        "configVersion": "string",
        "description": "string",
        "samlOptions": {
            "metadata": "string",
            "userAttribute": "string",
            "groupAttribute": "string",
            "openIDConnectProviderARN": "string",
            "sessionTimeout": "integer"
        },
        "createdDate": "long",
        "lastModifiedDate": "long"
    }
}
```

---

### 11.12 `delete-security-config`

Deletes a security configuration.

**Synopsis:**
```bash
aws opensearchserverless delete-security-config \
    --id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Security config ID |

**Output:** None

---

### 11.13 `get-security-config`

Returns details about a security configuration.

**Synopsis:**
```bash
aws opensearchserverless get-security-config \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Security config ID |

**Output Schema:**
```json
{
    "securityConfigDetail": {
        "id": "string",
        "type": "string",
        "configVersion": "string",
        "description": "string",
        "samlOptions": {},
        "iamIdentityCenterOptions": {},
        "createdDate": "long",
        "lastModifiedDate": "long"
    }
}
```

---

### 11.14 `list-security-configs`

Lists security configurations. **Paginated operation.**

**Synopsis:**
```bash
aws opensearchserverless list-security-configs \
    --type <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | `saml` or `iamidentitycenter` |

**Output Schema:**
```json
{
    "securityConfigSummaries": [
        {
            "id": "string",
            "type": "string",
            "configVersion": "string",
            "description": "string",
            "createdDate": "long",
            "lastModifiedDate": "long"
        }
    ],
    "nextToken": "string"
}
```

---

### 11.15 `update-security-config`

Updates a security configuration.

**Synopsis:**
```bash
aws opensearchserverless update-security-config \
    --id <value> \
    --config-version <value> \
    [--description <value>] \
    [--saml-options <value>] \
    [--iam-identity-center-options <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Security config ID |
| `--config-version` | **Yes** | string | -- | Current config version |
| `--description` | No | string | None | Updated description |
| `--saml-options` | No | structure | None | Updated SAML config |
| `--iam-identity-center-options` | No | structure | None | Updated IAM Identity Center config |

**Output Schema:**
```json
{
    "securityConfigDetail": {
        "id": "string",
        "type": "string",
        "configVersion": "string",
        "lastModifiedDate": "long"
    }
}
```
