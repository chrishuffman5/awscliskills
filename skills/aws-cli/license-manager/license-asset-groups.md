# License Asset Groups

### 5.1 `create-license-asset-group`

Creates a license asset group.

**Synopsis:**
```bash
aws license-manager create-license-asset-group \
    --name <value> \
    --license-asset-group-configurations <value> \
    --associated-license-asset-ruleset-arns <value> \
    --client-token <value> \
    [--description <value>] \
    [--properties <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Asset group name (max 128 chars) |
| `--license-asset-group-configurations` | **Yes** | list | -- | Configurations with `UsageDimension` |
| `--associated-license-asset-ruleset-arns` | **Yes** | list(string) | -- | ARNs of associated rulesets |
| `--client-token` | **Yes** | string | -- | Idempotency token |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--properties` | No | list | None | Key/Value properties |
| `--tags` | No | list | None | Tags (Key/Value pairs) |

**Output Schema:**
```json
{
    "LicenseAssetGroupArn": "string",
    "Status": "string"
}
```

---

### 5.2 `delete-license-asset-group`

Deletes a license asset group.

**Synopsis:**
```bash
aws license-manager delete-license-asset-group \
    --license-asset-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-asset-group-arn` | **Yes** | string | -- | ARN of the asset group to delete |

**Output:** None

---

### 5.3 `get-license-asset-group`

Gets details of a license asset group.

**Synopsis:**
```bash
aws license-manager get-license-asset-group \
    --license-asset-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-asset-group-arn` | **Yes** | string | -- | ARN of the asset group |

**Output Schema:**
```json
{
    "LicenseAssetGroup": {
        "LicenseAssetGroupArn": "string",
        "Name": "string",
        "Description": "string",
        "Status": "string",
        "LicenseAssetGroupConfigurations": [
            {
                "UsageDimension": "string"
            }
        ],
        "AssociatedLicenseAssetRulesetArns": ["string"],
        "Properties": [
            {
                "Key": "string",
                "Value": "string"
            }
        ],
        "Tags": []
    }
}
```

---

### 5.4 `list-license-asset-groups`

Lists license asset groups. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-license-asset-groups \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters to scope results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LicenseAssetGroups": [
        {
            "LicenseAssetGroupArn": "string",
            "Name": "string",
            "Status": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `update-license-asset-group`

Updates a license asset group.

**Synopsis:**
```bash
aws license-manager update-license-asset-group \
    --license-asset-group-arn <value> \
    [--name <value>] \
    [--description <value>] \
    [--license-asset-group-configurations <value>] \
    [--associated-license-asset-ruleset-arns <value>] \
    [--properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-asset-group-arn` | **Yes** | string | -- | ARN of the asset group |
| `--name` | No | string | None | New name |
| `--description` | No | string | None | New description |
| `--license-asset-group-configurations` | No | list | None | New configurations |
| `--associated-license-asset-ruleset-arns` | No | list(string) | None | New ruleset ARNs |
| `--properties` | No | list | None | New properties |

**Output:** None

---

### 5.6 `list-assets-for-license-asset-group`

Lists assets in a license asset group. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-assets-for-license-asset-group \
    --license-asset-group-arn <value> \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-asset-group-arn` | **Yes** | string | -- | ARN of the asset group |
| `--filters` | No | list | None | Filters to scope results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Assets": [
        {
            "AssetArn": "string",
            "AssetType": "string",
            "Properties": []
        }
    ],
    "NextToken": "string"
}
```

---

### 5.7 `create-license-asset-ruleset`

Creates a license asset ruleset.

**Synopsis:**
```bash
aws license-manager create-license-asset-ruleset \
    --name <value> \
    --license-asset-ruleset-type <value> \
    --rules <value> \
    --client-token <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Ruleset name |
| `--license-asset-ruleset-type` | **Yes** | string | -- | Ruleset type |
| `--rules` | **Yes** | list | -- | Ruleset rules |
| `--client-token` | **Yes** | string | -- | Idempotency token |
| `--description` | No | string | None | Description |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "LicenseAssetRulesetArn": "string",
    "Status": "string"
}
```

---

### 5.8 `delete-license-asset-ruleset`

Deletes a license asset ruleset.

**Synopsis:**
```bash
aws license-manager delete-license-asset-ruleset \
    --license-asset-ruleset-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-asset-ruleset-arn` | **Yes** | string | -- | ARN of the ruleset to delete |

**Output:** None

---

### 5.9 `get-license-asset-ruleset`

Gets details of a license asset ruleset.

**Synopsis:**
```bash
aws license-manager get-license-asset-ruleset \
    --license-asset-ruleset-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-asset-ruleset-arn` | **Yes** | string | -- | ARN of the ruleset |

**Output Schema:**
```json
{
    "LicenseAssetRuleset": {
        "LicenseAssetRulesetArn": "string",
        "Name": "string",
        "Description": "string",
        "LicenseAssetRulesetType": "string",
        "Rules": [],
        "Status": "string",
        "Tags": []
    }
}
```

---

### 5.10 `list-license-asset-rulesets`

Lists license asset rulesets. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-license-asset-rulesets \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters to scope results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LicenseAssetRulesets": [
        {
            "LicenseAssetRulesetArn": "string",
            "Name": "string",
            "Status": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.11 `update-license-asset-ruleset`

Updates a license asset ruleset.

**Synopsis:**
```bash
aws license-manager update-license-asset-ruleset \
    --license-asset-ruleset-arn <value> \
    [--name <value>] \
    [--description <value>] \
    [--rules <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-asset-ruleset-arn` | **Yes** | string | -- | ARN of the ruleset |
| `--name` | No | string | None | New name |
| `--description` | No | string | None | New description |
| `--rules` | No | list | None | New rules |

**Output:** None
