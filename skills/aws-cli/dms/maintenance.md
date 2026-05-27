# Maintenance

### 13.1 `apply-pending-maintenance-action`

Applies a pending maintenance action to a resource.

**Synopsis:**
```bash
aws dms apply-pending-maintenance-action \
    --replication-instance-arn <value> \
    --apply-action <value> \
    --opt-in-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-instance-arn` | **Yes** | string | -- | ARN of the replication instance |
| `--apply-action` | **Yes** | string | -- | Action to apply (e.g., `os-upgrade`, `system-update`, `db-upgrade`) |
| `--opt-in-type` | **Yes** | string | -- | `immediate`, `next-maintenance`, or `undo-opt-in` |

**Output Schema:**
```json
{
    "ResourcePendingMaintenanceActions": {
        "ResourceIdentifier": "string",
        "PendingMaintenanceActionDetails": [
            {
                "Action": "string",
                "AutoAppliedAfterDate": "timestamp",
                "ForcedApplyDate": "timestamp",
                "OptInStatus": "string",
                "CurrentApplyDate": "timestamp",
                "Description": "string"
            }
        ]
    }
}
```

---

### 13.2 `describe-pending-maintenance-actions`

Returns pending maintenance actions. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-pending-maintenance-actions \
    [--replication-instance-arn <value>] \
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
| `--replication-instance-arn` | No | string | -- | ARN of the replication instance |
| `--filters` | No | list | -- | Filters: `replication-instance-arn` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "PendingMaintenanceActions": [
        {
            "ResourceIdentifier": "string",
            "PendingMaintenanceActionDetails": [
                {
                    "Action": "string",
                    "AutoAppliedAfterDate": "timestamp",
                    "ForcedApplyDate": "timestamp",
                    "OptInStatus": "string",
                    "CurrentApplyDate": "timestamp",
                    "Description": "string"
                }
            ]
        }
    ],
    "Marker": "string"
}
```

---

### 13.3 `describe-account-attributes`

Lists all of the DMS attributes for the account, including resource quotas and unique account identifier.

**Synopsis:**
```bash
aws dms describe-account-attributes \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "AccountQuotas": [
        {
            "AccountQuotaName": "string",
            "Used": "long",
            "Max": "long"
        }
    ],
    "UniqueAccountIdentifier": "string"
}
```

---

### 13.4 `describe-engine-versions`

Returns information about available DMS engine versions. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-engine-versions \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "EngineVersions": [
        {
            "Version": "string",
            "Lifecycle": "string",
            "ReleaseStatus": "string",
            "LaunchDate": "timestamp",
            "AutoUpgradeDate": "timestamp",
            "DeprecationDate": "timestamp",
            "ForceUpgradeDate": "timestamp",
            "AvailableUpgrades": ["string"]
        }
    ],
    "Marker": "string"
}
```

---

### 13.5 `describe-conversion-configuration`

Returns the conversion configuration for a migration project.

**Synopsis:**
```bash
aws dms describe-conversion-configuration \
    --migration-project-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |

**Output Schema:**
```json
{
    "MigrationProjectIdentifier": "string",
    "ConversionConfiguration": "string"
}
```

---

### 13.6 `modify-conversion-configuration`

Modifies the conversion configuration for a migration project.

**Synopsis:**
```bash
aws dms modify-conversion-configuration \
    --migration-project-identifier <value> \
    --conversion-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--conversion-configuration` | **Yes** | string | -- | New conversion configuration JSON |

**Output Schema:**
```json
{
    "MigrationProjectIdentifier": "string"
}
```

---

### 13.7 `describe-extension-pack-associations`

Returns a paginated list of extension pack associations. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-extension-pack-associations \
    --migration-project-identifier <value> \
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
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--filters` | No | list | -- | Filters |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "Requests": [
        {
            "Status": "string",
            "RequestIdentifier": "string"
        }
    ]
}
```

---

### 13.8 `start-extension-pack-association`

Applies extension pack to the target database.

**Synopsis:**
```bash
aws dms start-extension-pack-association \
    --migration-project-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |

**Output Schema:**
```json
{
    "RequestIdentifier": "string"
}
```
