# Maintenance & Engine Info

### 11.1 `describe-pending-maintenance-actions`

Describes pending maintenance actions. **Paginated.**

```bash
aws rds describe-pending-maintenance-actions \
    [--resource-identifier <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-identifier` | No | string | all | Resource ARN filter |
| `--filters` | No | list | None | Filters: `db-cluster-id`, `db-instance-id` |

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

### 11.2 `apply-pending-maintenance-action`

Applies a pending maintenance action.

```bash
aws rds apply-pending-maintenance-action \
    --resource-identifier <value> \
    --apply-action <value> \
    --opt-in-type <value>
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--resource-identifier` | **Yes** | string | Resource ARN |
| `--apply-action` | **Yes** | string | Action to apply (e.g. `system-update`, `db-upgrade`) |
| `--opt-in-type` | **Yes** | string | `immediate`, `next-maintenance`, `undo-opt-in` |

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

### 11.3 `describe-db-engine-versions`

Describes available database engine versions. **Paginated.**

```bash
aws rds describe-db-engine-versions \
    [--engine <value>] \
    [--engine-version <value>] \
    [--db-parameter-group-family <value>] \
    [--filters <value>] \
    [--default-only | --no-default-only] \
    [--list-supported-character-sets | --no-list-supported-character-sets] \
    [--list-supported-timezones | --no-list-supported-timezones] \
    [--include-all | --no-include-all] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engine` | No | string | all | Engine filter |
| `--engine-version` | No | string | all | Version filter |
| `--db-parameter-group-family` | No | string | all | Family filter |
| `--default-only` / `--no-default-only` | No | boolean | false | Only default versions |
| `--include-all` / `--no-include-all` | No | boolean | false | Include all versions |

**Output Schema:**
```json
{
    "DBEngineVersions": [
        {
            "Engine": "string",
            "EngineVersion": "string",
            "DBParameterGroupFamily": "string",
            "DBEngineDescription": "string",
            "DBEngineVersionDescription": "string",
            "DefaultCharacterSet": {
                "CharacterSetName": "string",
                "CharacterSetDescription": "string"
            },
            "SupportedCharacterSets": [
                { "CharacterSetName": "string", "CharacterSetDescription": "string" }
            ],
            "SupportedTimezones": [
                { "TimezoneName": "string" }
            ],
            "ValidUpgradeTarget": [
                {
                    "Engine": "string",
                    "EngineVersion": "string",
                    "Description": "string",
                    "AutoUpgrade": "boolean",
                    "IsMajorVersionUpgrade": "boolean"
                }
            ],
            "ExportableLogTypes": ["string"],
            "SupportsLogExportsToCloudwatchLogs": "boolean",
            "SupportsReadReplica": "boolean",
            "SupportedEngineModes": ["string"],
            "Status": "string",
            "SupportsGlobalDatabases": "boolean",
            "TagList": [{ "Key": "string", "Value": "string" }]
        }
    ],
    "Marker": "string"
}
```

---

### 11.4 `describe-orderable-db-instance-options`

Describes available instance classes for an engine. **Paginated.**

```bash
aws rds describe-orderable-db-instance-options \
    --engine <value> \
    [--engine-version <value>] \
    [--db-instance-class <value>] \
    [--license-model <value>] \
    [--availability-zone-group <value>] \
    [--vpc | --no-vpc] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engine` | **Yes** | string | -- | Engine name |
| `--engine-version` | No | string | all | Version filter |
| `--db-instance-class` | No | string | all | Instance class filter |
| `--license-model` | No | string | all | License model filter |
| `--vpc` / `--no-vpc` | No | boolean | all | VPC filter |

**Output Schema:**
```json
{
    "OrderableDBInstanceOptions": [
        {
            "Engine": "string",
            "EngineVersion": "string",
            "DBInstanceClass": "string",
            "LicenseModel": "string",
            "AvailabilityZoneGroup": "string",
            "AvailabilityZones": [{ "Name": "string" }],
            "MultiAZCapable": "boolean",
            "ReadReplicaCapable": "boolean",
            "Vpc": "boolean",
            "SupportsStorageEncryption": "boolean",
            "StorageType": "string",
            "SupportsIops": "boolean",
            "SupportsEnhancedMonitoring": "boolean",
            "SupportsIAMDatabaseAuthentication": "boolean",
            "SupportsPerformanceInsights": "boolean",
            "MinStorageSize": "integer",
            "MaxStorageSize": "integer",
            "MinIopsPerDbInstance": "integer",
            "MaxIopsPerDbInstance": "integer",
            "MinIopsPerGib": "double",
            "MaxIopsPerGib": "double",
            "MinStorageThroughputPerDbInstance": "integer",
            "MaxStorageThroughputPerDbInstance": "integer",
            "SupportsGlobalDatabases": "boolean",
            "SupportsClusters": "boolean",
            "SupportsDedicatedLogVolume": "boolean"
        }
    ],
    "Marker": "string"
}
```

---

### 11.5 `describe-certificates`

Describes the available SSL/TLS certificates.

```bash
aws rds describe-certificates \
    [--certificate-identifier <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-identifier` | No | string | all | Specific certificate |

**Output Schema:**
```json
{
    "Certificates": [
        {
            "CertificateIdentifier": "string",
            "CertificateType": "string",
            "Thumbprint": "string",
            "ValidFrom": "timestamp",
            "ValidTill": "timestamp",
            "CertificateArn": "string",
            "CustomerOverride": "boolean",
            "CustomerOverrideValidTill": "timestamp"
        }
    ],
    "DefaultCertificateForNewLaunches": "string",
    "Marker": "string"
}
```

---
