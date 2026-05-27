# Upgrades

### 2.1 `upgrade-domain`

Upgrades an OpenSearch domain to a new engine version.

**Synopsis:**
```bash
aws opensearch upgrade-domain \
    --domain-name <value> \
    --target-version <value> \
    [--perform-check-only | --no-perform-check-only] \
    [--advanced-options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain to upgrade |
| `--target-version` | **Yes** | string | -- | Target engine version (e.g., `OpenSearch_2.13`) |
| `--perform-check-only` | No | boolean | false | Only validate eligibility without upgrading |
| `--advanced-options` | No | map | None | Advanced options for the upgrade |

**Output Schema:**
```json
{
    "UpgradeName": "string",
    "TargetVersion": "string",
    "PerformCheckOnly": "boolean",
    "DomainName": "string",
    "ChangeProgressDetails": {
        "ChangeId": "string",
        "Message": "string"
    }
}
```

---

### 2.2 `get-upgrade-status`

Returns the most recent upgrade status for a domain.

**Synopsis:**
```bash
aws opensearch get-upgrade-status \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |

**Output Schema:**
```json
{
    "UpgradeStep": "PRE_UPGRADE_CHECK|SNAPSHOT|UPGRADE",
    "StepStatus": "IN_PROGRESS|SUCCEEDED|SUCCEEDED_WITH_ISSUES|FAILED",
    "UpgradeName": "string"
}
```

---

### 2.3 `get-upgrade-history`

Returns the upgrade history for a domain. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch get-upgrade-history \
    --domain-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |

**Output Schema:**
```json
{
    "UpgradeHistories": [
        {
            "UpgradeName": "string",
            "StartTimestamp": "timestamp",
            "UpgradeStatus": "IN_PROGRESS|SUCCEEDED|SUCCEEDED_WITH_ISSUES|FAILED",
            "StepsList": [
                {
                    "UpgradeStep": "PRE_UPGRADE_CHECK|SNAPSHOT|UPGRADE",
                    "UpgradeStepStatus": "string",
                    "Issues": ["string"],
                    "ProgressPercent": "double"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `start-service-software-update`

Starts a service software update for a domain.

**Synopsis:**
```bash
aws opensearch start-service-software-update \
    --domain-name <value> \
    [--schedule-at <value>] \
    [--desired-start-time <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |
| `--schedule-at` | No | string | -- | `NOW`, `TIMESTAMP`, or `OFF_PEAK_WINDOW` |
| `--desired-start-time` | No | long | -- | Unix epoch timestamp for scheduled update |

**Output Schema:**
```json
{
    "ServiceSoftwareOptions": {
        "CurrentVersion": "string",
        "NewVersion": "string",
        "UpdateAvailable": "boolean",
        "Cancellable": "boolean",
        "UpdateStatus": "PENDING_UPDATE|IN_PROGRESS|COMPLETED|NOT_ELIGIBLE|ELIGIBLE",
        "Description": "string",
        "AutomatedUpdateDate": "timestamp",
        "OptionalDeployment": "boolean"
    }
}
```

---

### 2.5 `cancel-service-software-update`

Cancels a scheduled service software update.

**Synopsis:**
```bash
aws opensearch cancel-service-software-update \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |

**Output Schema:**
```json
{
    "ServiceSoftwareOptions": {
        "CurrentVersion": "string",
        "NewVersion": "string",
        "UpdateAvailable": "boolean",
        "Cancellable": "boolean",
        "UpdateStatus": "string"
    }
}
```

---

### 2.6 `list-scheduled-actions`

Lists scheduled actions for a domain. **Paginated operation.**

**Synopsis:**
```bash
aws opensearch list-scheduled-actions \
    --domain-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |

**Output Schema:**
```json
{
    "ScheduledActions": [
        {
            "Id": "string",
            "Type": "SERVICE_SOFTWARE_UPDATE|JVM_HEAP_SIZE_TUNING|JVM_YOUNG_GEN_TUNING",
            "Severity": "HIGH|MEDIUM|LOW",
            "ScheduledTime": "long",
            "Description": "string",
            "ScheduledBy": "CUSTOMER|SYSTEM",
            "Status": "PENDING_UPDATE|IN_PROGRESS|FAILED|COMPLETED|NOT_ELIGIBLE|ELIGIBLE",
            "Mandatory": "boolean",
            "Cancellable": "boolean"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.7 `update-scheduled-action`

Updates a scheduled action for a domain.

**Synopsis:**
```bash
aws opensearch update-scheduled-action \
    --domain-name <value> \
    --action-id <value> \
    --action-type <value> \
    --schedule-at <value> \
    [--desired-start-time <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Name of the domain |
| `--action-id` | **Yes** | string | -- | Action ID to update |
| `--action-type` | **Yes** | string | -- | `SERVICE_SOFTWARE_UPDATE`, `JVM_HEAP_SIZE_TUNING`, or `JVM_YOUNG_GEN_TUNING` |
| `--schedule-at` | **Yes** | string | -- | `NOW`, `TIMESTAMP`, or `OFF_PEAK_WINDOW` |
| `--desired-start-time` | No | long | -- | Unix epoch timestamp |

**Output Schema:**
```json
{
    "ScheduledAction": {
        "Id": "string",
        "Type": "string",
        "Severity": "string",
        "ScheduledTime": "long",
        "Status": "string"
    }
}
```
