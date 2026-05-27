# Rule Groups

### 2.1 `create-rule-group`

Creates a rule group. A rule group is a reusable collection of rules that can be referenced in web ACLs.

**Synopsis:**
```bash
aws wafv2 create-rule-group \
    --name <value> \
    --scope <value> \
    --capacity <value> \
    --visibility-config <value> \
    [--description <value>] \
    [--rules <value>] \
    [--tags <value>] \
    [--custom-response-bodies <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the rule group |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--capacity` | **Yes** | long | -- | WCU capacity for the rule group (immutable after creation) |
| `--visibility-config` | **Yes** | structure | -- | Visibility config |
| `--description` | No | string | -- | Description |
| `--rules` | No | list | -- | Rules in the group |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--custom-response-bodies` | No | map | -- | Custom response bodies |

**Output Schema:**
```json
{
    "Summary": {
        "Name": "string",
        "Id": "string",
        "Description": "string",
        "LockToken": "string",
        "ARN": "string"
    }
}
```

---

### 2.2 `delete-rule-group`

Deletes a rule group. Must not be referenced by any web ACL.

**Synopsis:**
```bash
aws wafv2 delete-rule-group \
    --name <value> \
    --scope <value> \
    --id <value> \
    --lock-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the rule group |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID of the rule group |
| `--lock-token` | **Yes** | string | -- | Lock token from get operation |

**Output:** None on success.

---

### 2.3 `get-rule-group`

Retrieves a rule group with full details.

**Synopsis:**
```bash
aws wafv2 get-rule-group \
    [--name <value>] \
    [--scope <value>] \
    [--id <value>] \
    [--arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | -- | Name of the rule group (use with scope and id) |
| `--scope` | No | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | No | string | -- | Unique ID of the rule group |
| `--arn` | No | string | -- | ARN of the rule group (alternative to name/scope/id) |

**Output Schema:**
```json
{
    "RuleGroup": {
        "Name": "string",
        "Id": "string",
        "Capacity": "long",
        "ARN": "string",
        "Description": "string",
        "Rules": [
            {
                "Name": "string",
                "Priority": "integer",
                "Statement": {},
                "Action": {},
                "VisibilityConfig": {},
                "RuleLabels": [],
                "CaptchaConfig": {},
                "ChallengeConfig": {}
            }
        ],
        "VisibilityConfig": {},
        "LabelNamespace": "string",
        "CustomResponseBodies": {},
        "AvailableLabels": [{"Name": "string"}],
        "ConsumedLabels": [{"Name": "string"}]
    },
    "LockToken": "string"
}
```

---

### 2.4 `list-rule-groups`

Returns a list of rule groups. **Paginated operation.**

**Synopsis:**
```bash
aws wafv2 list-rule-groups \
    --scope <value> \
    [--next-marker <value>] \
    [--limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--next-marker` | No | string | None | Pagination token |
| `--limit` | No | integer | None | Maximum results (1-100) |

**Output Schema:**
```json
{
    "NextMarker": "string",
    "RuleGroups": [
        {
            "Name": "string",
            "Id": "string",
            "Description": "string",
            "LockToken": "string",
            "ARN": "string"
        }
    ]
}
```

---

### 2.5 `update-rule-group`

Updates a rule group. Replaces the entire set of rules. Requires the current lock token.

**Synopsis:**
```bash
aws wafv2 update-rule-group \
    --name <value> \
    --scope <value> \
    --id <value> \
    --lock-token <value> \
    --visibility-config <value> \
    [--description <value>] \
    [--rules <value>] \
    [--custom-response-bodies <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the rule group |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID of the rule group |
| `--lock-token` | **Yes** | string | -- | Lock token from get operation |
| `--visibility-config` | **Yes** | structure | -- | Visibility config |
| `--description` | No | string | -- | New description |
| `--rules` | No | list | -- | New rules (replaces all existing) |
| `--custom-response-bodies` | No | map | -- | Custom response bodies |

**Output Schema:**
```json
{
    "NextLockToken": "string"
}
```

---

### 2.6 `list-available-managed-rule-groups`

Returns a list of the available AWS managed rule groups.

**Synopsis:**
```bash
aws wafv2 list-available-managed-rule-groups \
    --scope <value> \
    [--next-marker <value>] \
    [--limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--next-marker` | No | string | None | Pagination token |
| `--limit` | No | integer | None | Maximum results |

**Output Schema:**
```json
{
    "NextMarker": "string",
    "ManagedRuleGroups": [
        {
            "VendorName": "string",
            "Name": "string",
            "VersioningSupported": "boolean",
            "Description": "string"
        }
    ]
}
```

---

### 2.7 `list-available-managed-rule-group-versions`

Returns a list of available versions for a managed rule group.

**Synopsis:**
```bash
aws wafv2 list-available-managed-rule-group-versions \
    --vendor-name <value> \
    --name <value> \
    --scope <value> \
    [--next-marker <value>] \
    [--limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vendor-name` | **Yes** | string | -- | Vendor name (e.g., `AWS`) |
| `--name` | **Yes** | string | -- | Managed rule group name |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--next-marker` | No | string | None | Pagination token |
| `--limit` | No | integer | None | Maximum results |

**Output Schema:**
```json
{
    "NextMarker": "string",
    "Versions": [
        {
            "Name": "string",
            "LastUpdateTimestamp": "timestamp"
        }
    ],
    "CurrentDefaultVersion": "string"
}
```

---

### 2.8 `describe-managed-rule-group`

Returns details about a managed rule group, including the rules it contains.

**Synopsis:**
```bash
aws wafv2 describe-managed-rule-group \
    --vendor-name <value> \
    --name <value> \
    --scope <value> \
    [--version-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vendor-name` | **Yes** | string | -- | Vendor name (e.g., `AWS`) |
| `--name` | **Yes** | string | -- | Managed rule group name |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--version-name` | No | string | -- | Specific version (defaults to current default version) |

**Output Schema:**
```json
{
    "VersionName": "string",
    "SnsTopicArn": "string",
    "Capacity": "long",
    "Rules": [
        {
            "Name": "string",
            "Action": {
                "Block": {},
                "Allow": {},
                "Count": {},
                "Captcha": {},
                "Challenge": {}
            }
        }
    ],
    "LabelNamespace": "string",
    "AvailableLabels": [{"Name": "string"}],
    "ConsumedLabels": [{"Name": "string"}]
}
```

---

### 2.9 `get-managed-rule-set`

Retrieves a managed rule set. For use by managed rule group providers (marketplace sellers).

**Synopsis:**
```bash
aws wafv2 get-managed-rule-set \
    --name <value> \
    --scope <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the managed rule set |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID |

**Output Schema:**
```json
{
    "ManagedRuleSet": {
        "Name": "string",
        "Id": "string",
        "ARN": "string",
        "Description": "string",
        "PublishedVersions": {
            "string": {
                "AssociatedRuleGroupArn": "string",
                "Capacity": "long",
                "ForecastedLifetime": "integer",
                "PublishTimestamp": "timestamp",
                "LastUpdateTimestamp": "timestamp",
                "ExpiryTimestamp": "timestamp"
            }
        },
        "RecommendedVersion": "string",
        "LabelNamespace": "string"
    },
    "LockToken": "string"
}
```

---

### 2.10 `list-managed-rule-sets`

Lists managed rule sets. For use by managed rule group providers.

**Synopsis:**
```bash
aws wafv2 list-managed-rule-sets \
    --scope <value> \
    [--next-marker <value>] \
    [--limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--next-marker` | No | string | None | Pagination token |
| `--limit` | No | integer | None | Maximum results |

**Output Schema:**
```json
{
    "NextMarker": "string",
    "ManagedRuleSets": [
        {
            "Name": "string",
            "Id": "string",
            "Description": "string",
            "LockToken": "string",
            "ARN": "string",
            "LabelNamespace": "string"
        }
    ]
}
```

---

### 2.11 `put-managed-rule-set-versions`

Publishes versions of a managed rule set. For use by managed rule group providers.

**Synopsis:**
```bash
aws wafv2 put-managed-rule-set-versions \
    --name <value> \
    --scope <value> \
    --id <value> \
    --lock-token <value> \
    [--recommended-version <value>] \
    [--versions-to-publish <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the managed rule set |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID |
| `--lock-token` | **Yes** | string | -- | Lock token |
| `--recommended-version` | No | string | -- | Set the recommended version |
| `--versions-to-publish` | No | map | -- | Map of version name to publish config |

**Output Schema:**
```json
{
    "NextLockToken": "string"
}
```

---

### 2.12 `update-managed-rule-set-version-expiry-date`

Updates the expiry date for a version of a managed rule set. For use by managed rule group providers.

**Synopsis:**
```bash
aws wafv2 update-managed-rule-set-version-expiry-date \
    --name <value> \
    --scope <value> \
    --id <value> \
    --lock-token <value> \
    --version-to-expire <value> \
    --expiry-timestamp <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the managed rule set |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID |
| `--lock-token` | **Yes** | string | -- | Lock token |
| `--version-to-expire` | **Yes** | string | -- | Version to set expiry for |
| `--expiry-timestamp` | **Yes** | timestamp | -- | Expiry date/time |

**Output Schema:**
```json
{
    "ExpiringVersion": "string",
    "ExpiryTimestamp": "timestamp",
    "NextLockToken": "string"
}
```
