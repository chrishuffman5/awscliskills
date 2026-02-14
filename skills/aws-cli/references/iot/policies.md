# Policies

## 3.1 `create-policy`

Creates an IoT policy.

**Synopsis:**
```bash
aws iot create-policy \
    --policy-name <value> \
    --policy-document <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name (1-128 chars, pattern `[\w+=,.@-]+`) |
| `--policy-document` | **Yes** | string | -- | JSON policy document (max 2048 chars excl. whitespace) |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "policyName": "string",
    "policyArn": "string",
    "policyDocument": "string",
    "policyVersionId": "string"
}
```

---

## 3.2 `get-policy`

Gets an IoT policy.

**Synopsis:**
```bash
aws iot get-policy \
    --policy-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name |

**Output Schema:**
```json
{
    "policyName": "string",
    "policyArn": "string",
    "policyDocument": "string",
    "defaultVersionId": "string",
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp",
    "generationId": "string"
}
```

---

## 3.3 `list-policies`

Lists IoT policies. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-policies \
    [--marker <value>] \
    [--page-size <value>] \
    [--ascending-order | --no-ascending-order] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--marker` | No | string | None | Pagination marker |
| `--page-size` | No | integer | None | Max results per page |
| `--ascending-order` | No | boolean | false | Sort ascending |

**Output Schema:**
```json
{
    "policies": [
        {
            "policyName": "string",
            "policyArn": "string"
        }
    ],
    "nextMarker": "string"
}
```

---

## 3.4 `delete-policy`

Deletes an IoT policy. All versions must be deleted first (except default).

**Synopsis:**
```bash
aws iot delete-policy \
    --policy-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name |

**Output:** None

---

## 3.5 `create-policy-version`

Creates a new version of an IoT policy (max 5 versions).

**Synopsis:**
```bash
aws iot create-policy-version \
    --policy-name <value> \
    --policy-document <value> \
    [--set-as-default | --no-set-as-default] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name |
| `--policy-document` | **Yes** | string | -- | JSON policy document |
| `--set-as-default` | No | boolean | false | Set as the default version |

**Output Schema:**
```json
{
    "policyArn": "string",
    "policyDocument": "string",
    "policyVersionId": "string",
    "isDefaultVersion": "boolean"
}
```

---

## 3.6 `get-policy-version`

Gets a specific version of a policy.

**Synopsis:**
```bash
aws iot get-policy-version \
    --policy-name <value> \
    --policy-version-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name |
| `--policy-version-id` | **Yes** | string | -- | Policy version ID |

**Output Schema:**
```json
{
    "policyArn": "string",
    "policyName": "string",
    "policyDocument": "string",
    "policyVersionId": "string",
    "isDefaultVersion": "boolean",
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp",
    "generationId": "string"
}
```

---

## 3.7 `list-policy-versions`

Lists all versions of a policy.

**Synopsis:**
```bash
aws iot list-policy-versions \
    --policy-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name |

**Output Schema:**
```json
{
    "policyVersions": [
        {
            "versionId": "string",
            "isDefaultVersion": "boolean",
            "createDate": "timestamp"
        }
    ]
}
```

---

## 3.8 `delete-policy-version`

Deletes a policy version (cannot delete the default version).

**Synopsis:**
```bash
aws iot delete-policy-version \
    --policy-name <value> \
    --policy-version-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name |
| `--policy-version-id` | **Yes** | string | -- | Policy version ID |

**Output:** None

---

## 3.9 `set-default-policy-version`

Sets the default version of a policy.

**Synopsis:**
```bash
aws iot set-default-policy-version \
    --policy-name <value> \
    --policy-version-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name |
| `--policy-version-id` | **Yes** | string | -- | Version ID to set as default |

**Output:** None

---

## 3.10 `attach-policy`

Attaches a policy to a target (certificate ARN or thing group ARN).

**Synopsis:**
```bash
aws iot attach-policy \
    --policy-name <value> \
    --target <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name |
| `--target` | **Yes** | string | -- | Target ARN (certificate or thing group) |

**Output:** None

---

## 3.11 `detach-policy`

Detaches a policy from a target.

**Synopsis:**
```bash
aws iot detach-policy \
    --policy-name <value> \
    --target <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name |
| `--target` | **Yes** | string | -- | Target ARN |

**Output:** None

---

## 3.12 `list-attached-policies`

Lists policies attached to a target. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-attached-policies \
    --target <value> \
    [--recursive | --no-recursive] \
    [--marker <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target` | **Yes** | string | -- | Target ARN (certificate or thing group) |
| `--recursive` | No | boolean | false | Include inherited policies |
| `--marker` | No | string | None | Pagination marker |
| `--page-size` | No | integer | None | Max results per page |

**Output Schema:**
```json
{
    "policies": [
        {
            "policyName": "string",
            "policyArn": "string"
        }
    ],
    "nextMarker": "string"
}
```

---

## 3.13 `list-targets-for-policy`

Lists targets (certificates, thing groups) for a policy. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-targets-for-policy \
    --policy-name <value> \
    [--marker <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name |
| `--marker` | No | string | None | Pagination marker |
| `--page-size` | No | integer | None | Max results per page |

**Output Schema:**
```json
{
    "targets": ["string"],
    "nextMarker": "string"
}
```

---

## 3.14 `get-effective-policies`

Gets the effective policies for a thing or certificate.

**Synopsis:**
```bash
aws iot get-effective-policies \
    [--principal <value>] \
    [--cognito-identity-pool-id <value>] \
    [--thing-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--principal` | No | string | None | Principal ARN (certificate) |
| `--cognito-identity-pool-id` | No | string | None | Cognito identity pool ID |
| `--thing-name` | No | string | None | Thing name |

**Output Schema:**
```json
{
    "effectivePolicies": [
        {
            "policyName": "string",
            "policyArn": "string",
            "policyDocument": "string"
        }
    ]
}
```

---

## 3.15 `test-authorization`

Tests IoT policy authorization for actions and resources.

**Synopsis:**
```bash
aws iot test-authorization \
    --auth-infos <value> \
    [--principal <value>] \
    [--cognito-identity-pool-id <value>] \
    [--client-id <value>] \
    [--policy-names-to-add <value>] \
    [--policy-names-to-skip <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auth-infos` | **Yes** | list | -- | List of authorization info (actionType, resources) |
| `--principal` | No | string | None | Principal ARN |
| `--cognito-identity-pool-id` | No | string | None | Cognito pool ID |
| `--client-id` | No | string | None | MQTT client ID |
| `--policy-names-to-add` | No | list | None | Policies to add for testing |
| `--policy-names-to-skip` | No | list | None | Policies to skip for testing |

**AuthInfos structure:**
```json
[
    {
        "actionType": "PUBLISH|SUBSCRIBE|RECEIVE|CONNECT",
        "resources": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "authResults": [
        {
            "authInfo": {"actionType": "string", "resources": ["string"]},
            "allowed": {"policies": [{"policyName": "string", "policyArn": "string"}]},
            "denied": {
                "implicitDeny": {"policies": []},
                "explicitDeny": {"policies": []}
            },
            "authDecision": "ALLOWED|EXPLICIT_DENY|IMPLICIT_DENY",
            "missingContextValues": ["string"]
        }
    ]
}
```
