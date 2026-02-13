# Parameter Groups

### 4.1 `create-db-parameter-group`

Creates a DB parameter group.

**Synopsis:**
```bash
aws rds create-db-parameter-group \
    --db-parameter-group-name <value> \
    --db-parameter-group-family <value> \
    --description <value> \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-parameter-group-name` | **Yes** | string | Parameter group name (1-255 chars) |
| `--db-parameter-group-family` | **Yes** | string | Family (e.g. `postgres16`, `mysql8.0`, `aurora-postgresql16`) |
| `--description` | **Yes** | string | Description |
| `--tags` | No | list | Tags |

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

### 4.2 `delete-db-parameter-group`

Deletes a DB parameter group.

**Synopsis:**
```bash
aws rds delete-db-parameter-group \
    --db-parameter-group-name <value>
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-parameter-group-name` | **Yes** | string | Parameter group name |

**Output:** None on success.

---

### 4.3 `describe-db-parameter-groups`

Describes DB parameter groups. **Paginated.**

**Synopsis:**
```bash
aws rds describe-db-parameter-groups \
    [--db-parameter-group-name <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-parameter-group-name` | No | string | all | Specific group name |
| `--filters` | No | list | None | Filters: `db-parameter-group-name` |
| `--max-items` | No | integer | None | Total items |
| `--starting-token` | No | string | None | Pagination token |

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
    ],
    "Marker": "string"
}
```

---

### 4.4 `describe-db-parameters`

Lists parameters in a DB parameter group. **Paginated.**

**Synopsis:**
```bash
aws rds describe-db-parameters \
    --db-parameter-group-name <value> \
    [--source <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-parameter-group-name` | **Yes** | string | -- | Parameter group name |
| `--source` | No | string | all | Filter: `user`, `system`, `engine-default` |
| `--filters` | No | list | None | Filters |
| `--max-items` | No | integer | None | Total items |
| `--starting-token` | No | string | None | Pagination token |

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
            "MinimumEngineVersion": "string",
            "ApplyMethod": "immediate|pending-reboot",
            "SupportedEngineModes": ["string"]
        }
    ],
    "Marker": "string"
}
```

---

### 4.5 `modify-db-parameter-group`

Modifies parameters in a DB parameter group.

**Synopsis:**
```bash
aws rds modify-db-parameter-group \
    --db-parameter-group-name <value> \
    --parameters <value>
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-parameter-group-name` | **Yes** | string | Parameter group name |
| `--parameters` | **Yes** | list | Parameters to modify. Shorthand: `ParameterName=string,ParameterValue=string,ApplyMethod=immediate\|pending-reboot ...` |

**Output Schema:**
```json
{
    "DBParameterGroupName": "string"
}
```

---

### 4.6 `reset-db-parameter-group`

Resets parameters to their default values.

**Synopsis:**
```bash
aws rds reset-db-parameter-group \
    --db-parameter-group-name <value> \
    [--reset-all-parameters | --no-reset-all-parameters] \
    [--parameters <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-parameter-group-name` | **Yes** | string | -- | Parameter group name |
| `--reset-all-parameters` / `--no-reset-all-parameters` | No | boolean | false | Reset all parameters |
| `--parameters` | No | list | None | Specific parameters to reset |

**Output Schema:**
```json
{
    "DBParameterGroupName": "string"
}
```

---

### 4.7 `create-db-cluster-parameter-group`

Creates an Aurora cluster parameter group.

**Synopsis:**
```bash
aws rds create-db-cluster-parameter-group \
    --db-cluster-parameter-group-name <value> \
    --db-parameter-group-family <value> \
    --description <value> \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-cluster-parameter-group-name` | **Yes** | string | Group name |
| `--db-parameter-group-family` | **Yes** | string | Family (e.g. `aurora-postgresql16`) |
| `--description` | **Yes** | string | Description |
| `--tags` | No | list | Tags |

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

### 4.8 `delete-db-cluster-parameter-group`

Deletes an Aurora cluster parameter group.

```bash
aws rds delete-db-cluster-parameter-group \
    --db-cluster-parameter-group-name <value>
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-cluster-parameter-group-name` | **Yes** | string | Group name |

**Output:** None on success.

---

### 4.9 `describe-db-cluster-parameter-groups`

Describes Aurora cluster parameter groups. **Paginated.**

```bash
aws rds describe-db-cluster-parameter-groups \
    [--db-cluster-parameter-group-name <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

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
    ],
    "Marker": "string"
}
```

---

### 4.10 `describe-db-cluster-parameters`

Lists parameters in a cluster parameter group. **Paginated.**

```bash
aws rds describe-db-cluster-parameters \
    --db-cluster-parameter-group-name <value> \
    [--source <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-cluster-parameter-group-name` | **Yes** | string | Group name |
| `--source` | No | string | `user`, `system`, `engine-default` |

**Output Schema:** Same `Parameters` structure as `describe-db-parameters`.

---

### 4.11 `modify-db-cluster-parameter-group`

Modifies parameters in a cluster parameter group.

```bash
aws rds modify-db-cluster-parameter-group \
    --db-cluster-parameter-group-name <value> \
    --parameters <value>
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-cluster-parameter-group-name` | **Yes** | string | Group name |
| `--parameters` | **Yes** | list | `ParameterName=string,ParameterValue=string,ApplyMethod=immediate\|pending-reboot ...` |

**Output Schema:**
```json
{
    "DBClusterParameterGroupName": "string"
}
```

---

### 4.12 `reset-db-cluster-parameter-group`

Resets cluster parameter group to defaults.

```bash
aws rds reset-db-cluster-parameter-group \
    --db-cluster-parameter-group-name <value> \
    [--reset-all-parameters | --no-reset-all-parameters] \
    [--parameters <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-parameter-group-name` | **Yes** | string | -- | Group name |
| `--reset-all-parameters` / `--no-reset-all-parameters` | No | boolean | false | Reset all |
| `--parameters` | No | list | None | Specific parameters to reset |

**Output Schema:**
```json
{
    "DBClusterParameterGroupName": "string"
}
```

---
