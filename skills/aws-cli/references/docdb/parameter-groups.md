# Parameter Groups

### 4.1 `create-db-cluster-parameter-group`

Creates a new cluster parameter group. Parameters in a cluster parameter group apply to all instances in the cluster.

**Synopsis:**
```bash
aws docdb create-db-cluster-parameter-group \
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
| `--db-parameter-group-family` | **Yes** | string | -- | Parameter group family (e.g., `docdb5.0`, `docdb4.0`, `docdb3.6`) |
| `--description` | **Yes** | string | -- | Description for the parameter group |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

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

### 4.2 `delete-db-cluster-parameter-group`

Deletes a cluster parameter group. The default parameter group cannot be deleted.

**Synopsis:**
```bash
aws docdb delete-db-cluster-parameter-group \
    --db-cluster-parameter-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-parameter-group-name` | **Yes** | string | -- | Parameter group name to delete |

**Output:** None (HTTP 200 on success)

---

### 4.3 `describe-db-cluster-parameter-groups`

Returns a list of cluster parameter group descriptions. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-db-cluster-parameter-groups \
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
| `--db-cluster-parameter-group-name` | No | string | All | Parameter group name |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

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

### 4.4 `describe-db-cluster-parameters`

Returns the detailed parameter list for a cluster parameter group. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-db-cluster-parameters \
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
| `--source` | No | string | All | Filter by source: `user`, `system`, `engine-default` |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

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
            "IsModifiable": true|false,
            "ApplyMethod": "immediate|pending-reboot"
        }
    ],
    "Marker": "string"
}
```

---

### 4.5 `modify-db-cluster-parameter-group`

Modifies the parameters of a cluster parameter group.

**Synopsis:**
```bash
aws docdb modify-db-cluster-parameter-group \
    --db-cluster-parameter-group-name <value> \
    --parameters <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-cluster-parameter-group-name` | **Yes** | string | -- | Parameter group name |
| `--parameters` | **Yes** | list | -- | Parameters to modify. Shorthand: `ParameterName=string,ParameterValue=string,ApplyMethod=immediate\|pending-reboot ...` |

**Output Schema:**
```json
{
    "DBClusterParameterGroupName": "string"
}
```

---

### 4.6 `reset-db-cluster-parameter-group`

Resets parameters in a cluster parameter group to their default values.

**Synopsis:**
```bash
aws docdb reset-db-cluster-parameter-group \
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
| `--parameters` | No | list | None | Specific parameters to reset |

**Output Schema:**
```json
{
    "DBClusterParameterGroupName": "string"
}
```

---

### 4.7 `copy-db-cluster-parameter-group`

Copies a cluster parameter group.

**Synopsis:**
```bash
aws docdb copy-db-cluster-parameter-group \
    --source-db-cluster-parameter-group-identifier <value> \
    --target-db-cluster-parameter-group-identifier <value> \
    --target-db-cluster-parameter-group-description <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-db-cluster-parameter-group-identifier` | **Yes** | string | -- | Source parameter group identifier or ARN |
| `--target-db-cluster-parameter-group-identifier` | **Yes** | string | -- | Target parameter group identifier |
| `--target-db-cluster-parameter-group-description` | **Yes** | string | -- | Description for the copied group |
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
