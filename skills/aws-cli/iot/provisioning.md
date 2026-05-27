# Provisioning

## 12.1 `create-provisioning-template`

Creates a fleet provisioning template.

**Synopsis:**
```bash
aws iot create-provisioning-template \
    --template-name <value> \
    --template-body <value> \
    --provisioning-role-arn <value> \
    [--description <value>] \
    [--enabled | --no-enabled] \
    [--pre-provisioning-hook <value>] \
    [--type <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name (1-36 chars) |
| `--template-body` | **Yes** | string | -- | JSON template body (max 10240 chars) |
| `--provisioning-role-arn` | **Yes** | string | -- | IAM role ARN (20-2048 chars) |
| `--description` | No | string | None | Description (max 500 chars) |
| `--enabled` | No | boolean | false | Enable the template |
| `--pre-provisioning-hook` | No | structure | None | Lambda pre-provisioning hook |
| `--type` | No | string | FLEET_PROVISIONING | `FLEET_PROVISIONING` or `JITP` |
| `--tags` | No | list | None | Tags |

**PreProvisioningHook:**
```json
{
    "payloadVersion": "string",
    "targetArn": "string"
}
```

**Output Schema:**
```json
{
    "templateArn": "string",
    "templateName": "string",
    "defaultVersionId": "integer"
}
```

---

## 12.2 `describe-provisioning-template`

Describes a provisioning template.

**Synopsis:**
```bash
aws iot describe-provisioning-template \
    --template-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |

**Output Schema:**
```json
{
    "templateArn": "string",
    "templateName": "string",
    "description": "string",
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp",
    "defaultVersionId": "integer",
    "templateBody": "string",
    "enabled": "boolean",
    "provisioningRoleArn": "string",
    "preProvisioningHook": {},
    "type": "FLEET_PROVISIONING|JITP"
}
```

---

## 12.3 `list-provisioning-templates`

Lists provisioning templates. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-provisioning-templates \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results (1-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "templates": [
        {
            "templateArn": "string",
            "templateName": "string",
            "description": "string",
            "creationDate": "timestamp",
            "lastModifiedDate": "timestamp",
            "enabled": "boolean",
            "type": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 12.4 `update-provisioning-template`

Updates a provisioning template.

**Synopsis:**
```bash
aws iot update-provisioning-template \
    --template-name <value> \
    [--description <value>] \
    [--enabled | --no-enabled] \
    [--default-version-id <value>] \
    [--provisioning-role-arn <value>] \
    [--pre-provisioning-hook <value>] \
    [--remove-pre-provisioning-hook | --no-remove-pre-provisioning-hook] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--description` | No | string | None | Updated description |
| `--enabled` | No | boolean | None | Enable/disable |
| `--default-version-id` | No | integer | None | Set default version |
| `--provisioning-role-arn` | No | string | None | Updated role ARN |
| `--pre-provisioning-hook` | No | structure | None | Updated hook |
| `--remove-pre-provisioning-hook` | No | boolean | false | Remove hook |

**Output:** None

---

## 12.5 `delete-provisioning-template`

Deletes a provisioning template.

**Synopsis:**
```bash
aws iot delete-provisioning-template \
    --template-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |

**Output:** None

---

## 12.6 `create-provisioning-template-version`

Creates a new version of a provisioning template.

**Synopsis:**
```bash
aws iot create-provisioning-template-version \
    --template-name <value> \
    --template-body <value> \
    [--set-as-default | --no-set-as-default] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--template-body` | **Yes** | string | -- | Template body JSON |
| `--set-as-default` | No | boolean | false | Set as default version |

**Output Schema:**
```json
{
    "templateArn": "string",
    "templateName": "string",
    "versionId": "integer",
    "isDefaultVersion": "boolean"
}
```

---

## 12.7 `describe-provisioning-template-version`

Describes a provisioning template version.

**Synopsis:**
```bash
aws iot describe-provisioning-template-version \
    --template-name <value> \
    --version-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--version-id` | **Yes** | integer | -- | Version ID |

**Output Schema:**
```json
{
    "versionId": "integer",
    "creationDate": "timestamp",
    "templateBody": "string",
    "isDefaultVersion": "boolean"
}
```

---

## 12.8 `list-provisioning-template-versions`

Lists provisioning template versions. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-provisioning-template-versions \
    --template-name <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "versions": [
        {
            "versionId": "integer",
            "creationDate": "timestamp",
            "isDefaultVersion": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

## 12.9 `delete-provisioning-template-version`

Deletes a provisioning template version.

**Synopsis:**
```bash
aws iot delete-provisioning-template-version \
    --template-name <value> \
    --version-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--version-id` | **Yes** | integer | -- | Version ID |

**Output:** None

---

## 12.10 `create-provisioning-claim`

Creates a provisioning claim for claim-based provisioning.

**Synopsis:**
```bash
aws iot create-provisioning-claim \
    --template-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |

**Output Schema:**
```json
{
    "certificateId": "string",
    "certificatePem": "string",
    "keyPair": {
        "PublicKey": "string",
        "PrivateKey": "string"
    },
    "expiration": "timestamp"
}
```
