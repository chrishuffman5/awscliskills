# Parameter Groups

### 5.1 `create-db-cluster-parameter-group`

Creates a new Neptune DB cluster parameter group.

**Synopsis:**
```bash
aws neptune create-db-cluster-parameter-group \
    --db-cluster-parameter-group-name <value> \
    --db-parameter-group-family <value> \
    --description <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-parameter-group-name` | **Yes** | string | -- | Parameter group name |
| `--db-parameter-group-family` | **Yes** | string | -- | Family (e.g., `neptune1`, `neptune1.3`) |
| `--description` | **Yes** | string | -- | Description |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "DBClusterParameterGroup": {
        "DBClusterParameterGroupName": "string",
        "DBParameterGroupFamily": "string",
        "Description": "string",
        "DBClusterParameterGroupArn": "string"
    }
}
```

---

### 5.2 `modify-db-cluster-parameter-group`

Modifies parameters in a Neptune DB cluster parameter group.

**Synopsis:**
```bash
aws neptune modify-db-cluster-parameter-group \
    --db-cluster-parameter-group-name <value> \
    --parameters <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-parameter-group-name` | **Yes** | string | -- | Parameter group name |
| `--parameters` | **Yes** | list | -- | Parameters. Shorthand: `ParameterName=string,ParameterValue=string,ApplyMethod=string ...` |

Apply methods: `immediate`, `pending-reboot`

**Output Schema:**
```json
{
    "DBClusterParameterGroupName": "string"
}
```

---

### 5.3 `delete-db-cluster-parameter-group`

Deletes a Neptune DB cluster parameter group.

**Synopsis:**
```bash
aws neptune delete-db-cluster-parameter-group \
    --db-cluster-parameter-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-parameter-group-name` | **Yes** | string | -- | Parameter group name |

**Output:** None

---

### 5.4 `describe-db-cluster-parameter-groups`

Describes Neptune DB cluster parameter groups. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-db-cluster-parameter-groups \
    [--db-cluster-parameter-group-name <value>] \
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
| `--db-cluster-parameter-group-name` | No | string | -- | Specific parameter group to describe |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "DBClusterParameterGroups": [
        {
            "DBClusterParameterGroupName": "string",
            "DBParameterGroupFamily": "string",
            "Description": "string",
            "DBClusterParameterGroupArn": "string"
        }
    ]
}
```

---

### 5.5 `describe-db-cluster-parameters`

Describes parameters in a Neptune DB cluster parameter group. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-db-cluster-parameters \
    --db-cluster-parameter-group-name <value> \
    [--source <value>] \
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
| `--db-cluster-parameter-group-name` | **Yes** | string | -- | Parameter group name |
| `--source` | No | string | -- | Filter: `user`, `system`, `engine-default` |

**Output Schema:**
```json
{
    "Parameters": [
        {
            "ParameterName": "string",
            "ParameterValue": "string",
            "Description": "string",
            "Source": "string",
            "ApplyType": "string",
            "DataType": "string",
            "AllowedValues": "string",
            "IsModifiable": "boolean",
            "ApplyMethod": "string"
        }
    ]
}
```

---

### 5.6 `reset-db-cluster-parameter-group`

Resets parameters in a Neptune DB cluster parameter group to defaults.

**Synopsis:**
```bash
aws neptune reset-db-cluster-parameter-group \
    --db-cluster-parameter-group-name <value> \
    [--reset-all-parameters | --no-reset-all-parameters] \
    [--parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-parameter-group-name` | **Yes** | string | -- | Parameter group name |
| `--reset-all-parameters` | No | boolean | false | Reset all parameters to defaults |
| `--parameters` | No | list | -- | Specific parameters to reset |

**Output Schema:**
```json
{
    "DBClusterParameterGroupName": "string"
}
```

---

### 5.7 `describe-engine-default-cluster-parameters`

Returns default engine and system parameter information for a cluster parameter group.

**Synopsis:**
```bash
aws neptune describe-engine-default-cluster-parameters \
    --db-parameter-group-family <value> \
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
| `--db-parameter-group-family` | **Yes** | string | -- | Parameter group family (e.g., `neptune1.3`) |

**Output Schema:**
```json
{
    "EngineDefaults": {
        "DBParameterGroupFamily": "string",
        "Parameters": [
            {
                "ParameterName": "string",
                "ParameterValue": "string",
                "Description": "string",
                "Source": "string",
                "DataType": "string",
                "AllowedValues": "string",
                "IsModifiable": "boolean"
            }
        ]
    }
}
```

---

### 5.8 `create-db-parameter-group`

Creates a new Neptune DB instance parameter group.

**Synopsis:**
```bash
aws neptune create-db-parameter-group \
    --db-parameter-group-name <value> \
    --db-parameter-group-family <value> \
    --description <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-parameter-group-name` | **Yes** | string | -- | Parameter group name |
| `--db-parameter-group-family` | **Yes** | string | -- | Family (e.g., `neptune1`, `neptune1.3`) |
| `--description` | **Yes** | string | -- | Description |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "DBParameterGroup": {
        "DBParameterGroupName": "string",
        "DBParameterGroupFamily": "string",
        "Description": "string",
        "DBParameterGroupArn": "string"
    }
}
```

---

### 5.9 `modify-db-parameter-group`

Modifies parameters in a Neptune DB instance parameter group.

**Synopsis:**
```bash
aws neptune modify-db-parameter-group \
    --db-parameter-group-name <value> \
    --parameters <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-parameter-group-name` | **Yes** | string | -- | Parameter group name |
| `--parameters` | **Yes** | list | -- | Parameters. Shorthand: `ParameterName=string,ParameterValue=string,ApplyMethod=string ...` |

**Output Schema:**
```json
{
    "DBParameterGroupName": "string"
}
```

---

### 5.10 `delete-db-parameter-group`

Deletes a Neptune DB instance parameter group.

**Synopsis:**
```bash
aws neptune delete-db-parameter-group \
    --db-parameter-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-parameter-group-name` | **Yes** | string | -- | Parameter group name |

**Output:** None

---

### 5.11 `describe-db-parameter-groups`

Describes Neptune DB instance parameter groups. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-db-parameter-groups \
    [--db-parameter-group-name <value>] \
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
| `--db-parameter-group-name` | No | string | -- | Specific parameter group to describe |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "DBParameterGroups": [
        {
            "DBParameterGroupName": "string",
            "DBParameterGroupFamily": "string",
            "Description": "string",
            "DBParameterGroupArn": "string"
        }
    ]
}
```

---

### 5.12 `describe-db-parameters`

Describes parameters in a Neptune DB instance parameter group. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-db-parameters \
    --db-parameter-group-name <value> \
    [--source <value>] \
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
| `--db-parameter-group-name` | **Yes** | string | -- | Parameter group name |
| `--source` | No | string | -- | Filter: `user`, `system`, `engine-default` |

**Output Schema:**
```json
{
    "Parameters": [
        {
            "ParameterName": "string",
            "ParameterValue": "string",
            "Description": "string",
            "Source": "string",
            "ApplyType": "string",
            "DataType": "string",
            "AllowedValues": "string",
            "IsModifiable": "boolean",
            "ApplyMethod": "string"
        }
    ]
}
```

---

### 5.13 `reset-db-parameter-group`

Resets parameters in a Neptune DB instance parameter group to defaults.

**Synopsis:**
```bash
aws neptune reset-db-parameter-group \
    --db-parameter-group-name <value> \
    [--reset-all-parameters | --no-reset-all-parameters] \
    [--parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-parameter-group-name` | **Yes** | string | -- | Parameter group name |
| `--reset-all-parameters` | No | boolean | false | Reset all parameters to defaults |
| `--parameters` | No | list | -- | Specific parameters to reset |

**Output Schema:**
```json
{
    "DBParameterGroupName": "string"
}
```

---

### 5.14 `describe-engine-default-parameters`

Returns default engine and system parameter information for an instance parameter group.

**Synopsis:**
```bash
aws neptune describe-engine-default-parameters \
    --db-parameter-group-family <value> \
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
| `--db-parameter-group-family` | **Yes** | string | -- | Parameter group family (e.g., `neptune1.3`) |

**Output Schema:**
```json
{
    "EngineDefaults": {
        "DBParameterGroupFamily": "string",
        "Parameters": [
            {
                "ParameterName": "string",
                "ParameterValue": "string",
                "Description": "string",
                "Source": "string",
                "DataType": "string",
                "AllowedValues": "string",
                "IsModifiable": "boolean"
            }
        ]
    }
}
```
