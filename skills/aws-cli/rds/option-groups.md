# Option Groups

### 6.1 `create-option-group`

Creates an option group.

```bash
aws rds create-option-group \
    --option-group-name <value> \
    --engine-name <value> \
    --major-engine-version <value> \
    --option-group-description <value> \
    [--tags <value>]
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--option-group-name` | **Yes** | string | Option group name (1-255 chars) |
| `--engine-name` | **Yes** | string | Engine (e.g. `oracle-ee`, `sqlserver-ee`, `mysql`) |
| `--major-engine-version` | **Yes** | string | Major engine version (e.g. `19`, `15.00`) |
| `--option-group-description` | **Yes** | string | Description |
| `--tags` | No | list | Tags |

**Output Schema:**
```json
{
    "OptionGroup": {
        "OptionGroupName": "string",
        "OptionGroupDescription": "string",
        "EngineName": "string",
        "MajorEngineVersion": "string",
        "Options": [
            {
                "OptionName": "string",
                "OptionDescription": "string",
                "Persistent": "boolean",
                "Permanent": "boolean",
                "Port": "integer",
                "OptionVersion": "string",
                "OptionSettings": [
                    {
                        "Name": "string",
                        "Value": "string",
                        "DefaultValue": "string",
                        "Description": "string",
                        "ApplyType": "string",
                        "DataType": "string",
                        "AllowedValues": "string",
                        "IsModifiable": "boolean",
                        "IsCollection": "boolean"
                    }
                ],
                "DBSecurityGroupMemberships": [
                    { "DBSecurityGroupName": "string", "Status": "string" }
                ],
                "VpcSecurityGroupMemberships": [
                    { "VpcSecurityGroupId": "string", "Status": "string" }
                ]
            }
        ],
        "AllowsVpcAndNonVpcInstanceMemberships": "boolean",
        "VpcId": "string",
        "OptionGroupArn": "string",
        "SourceOptionGroup": "string",
        "SourceAccountId": "string"
    }
}
```

---

### 6.2 `delete-option-group`

Deletes an option group.

```bash
aws rds delete-option-group \
    --option-group-name <value>
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--option-group-name` | **Yes** | string | Option group name |

**Output:** None on success.

---

### 6.3 `describe-option-groups`

Describes option groups. **Paginated.**

```bash
aws rds describe-option-groups \
    [--option-group-name <value>] \
    [--engine-name <value>] \
    [--major-engine-version <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--option-group-name` | No | string | all | Specific group |
| `--engine-name` | No | string | all | Filter by engine |
| `--major-engine-version` | No | string | all | Filter by version |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "OptionGroupsList": [
        { "...same OptionGroup structure..." }
    ],
    "Marker": "string"
}
```

---

### 6.4 `describe-option-group-options`

Describes available options for a given engine/version.

```bash
aws rds describe-option-group-options \
    --engine-name <value> \
    [--major-engine-version <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--engine-name` | **Yes** | string | Engine name |
| `--major-engine-version` | No | string | Major version filter |

**Output Schema:**
```json
{
    "OptionGroupOptions": [
        {
            "Name": "string",
            "Description": "string",
            "EngineName": "string",
            "MajorEngineVersion": "string",
            "MinimumRequiredMinorEngineVersion": "string",
            "PortRequired": "boolean",
            "DefaultPort": "integer",
            "OptionsDependedOn": ["string"],
            "OptionsConflictsWith": ["string"],
            "Persistent": "boolean",
            "Permanent": "boolean",
            "RequiresAutoMinorEngineVersionUpgrade": "boolean",
            "VpcOnly": "boolean",
            "OptionGroupOptionSettings": [
                {
                    "SettingName": "string",
                    "SettingDescription": "string",
                    "DefaultValue": "string",
                    "ApplyType": "string",
                    "AllowedValues": "string",
                    "IsModifiable": "boolean",
                    "IsRequired": "boolean",
                    "MinimumEngineVersionPerAllowedValue": [
                        { "AllowedValue": "string", "MinimumEngineVersion": "string" }
                    ]
                }
            ]
        }
    ],
    "Marker": "string"
}
```

---

### 6.5 `modify-option-group`

Modifies an option group (add or remove options).

```bash
aws rds modify-option-group \
    --option-group-name <value> \
    [--options-to-include <value>] \
    [--options-to-remove <value>] \
    [--apply-immediately | --no-apply-immediately]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--option-group-name` | **Yes** | string | -- | Option group name |
| `--options-to-include` | No | list | None | Options to add (complex structure) |
| `--options-to-remove` | No | list | None | Option names to remove |
| `--apply-immediately` / `--no-apply-immediately` | No | boolean | false | Apply now |

**Output Schema:** Same `OptionGroup` structure.

---

### 6.6 `copy-option-group`

Copies an option group.

```bash
aws rds copy-option-group \
    --source-option-group-identifier <value> \
    --target-option-group-identifier <value> \
    --target-option-group-description <value> \
    [--tags <value>]
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--source-option-group-identifier` | **Yes** | string | Source group identifier or ARN |
| `--target-option-group-identifier` | **Yes** | string | Target group identifier |
| `--target-option-group-description` | **Yes** | string | Description for the copy |
| `--tags` | No | list | Tags |

**Output Schema:** Same `OptionGroup` structure.

---
