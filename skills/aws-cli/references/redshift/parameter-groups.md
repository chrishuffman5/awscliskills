# Parameter Groups

### 3.1 `create-cluster-parameter-group`

Creates a new Amazon Redshift parameter group.

**Synopsis:**
```bash
aws redshift create-cluster-parameter-group \
    --parameter-group-name <value> \
    --parameter-group-family <value> \
    --description <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--parameter-group-name` | **Yes** | string | -- | Name for the parameter group (max 255 chars) |
| `--parameter-group-family` | **Yes** | string | -- | Parameter group family (e.g., `redshift-1.0`) |
| `--description` | **Yes** | string | -- | Description of the parameter group |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "ClusterParameterGroup": {
        "ParameterGroupName": "string",
        "ParameterGroupFamily": "string",
        "Description": "string",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 3.2 `delete-cluster-parameter-group`

Deletes a specified Amazon Redshift parameter group.

**Synopsis:**
```bash
aws redshift delete-cluster-parameter-group \
    --parameter-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--parameter-group-name` | **Yes** | string | -- | Parameter group to delete |

No output on success.

---

### 3.3 `describe-cluster-parameter-groups`

Returns a list of parameter groups. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-cluster-parameter-groups \
    [--parameter-group-name <value>] \
    [--tag-keys <value>] \
    [--tag-values <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--parameter-group-name` | No | string | -- | Specific parameter group |
| `--tag-keys` | No | list(string) | -- | Filter by tag keys |
| `--tag-values` | No | list(string) | -- | Filter by tag values |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "ParameterGroups": [
        {
            "ParameterGroupName": "string",
            "ParameterGroupFamily": "string",
            "Description": "string",
            "Tags": [{"Key": "string", "Value": "string"}]
        }
    ],
    "Marker": "string"
}
```

---

### 3.4 `describe-cluster-parameters`

Returns detailed parameter information for a specified parameter group. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-cluster-parameters \
    --parameter-group-name <value> \
    [--source <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--parameter-group-name` | **Yes** | string | -- | Parameter group to describe |
| `--source` | No | string | -- | Filter: `user`, `engine-default` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Parameters": [
        {
            "ParameterName": "string",
            "ParameterValue": "string",
            "Description": "string",
            "Source": "engine-default|user",
            "DataType": "string",
            "AllowedValues": "string",
            "ApplyType": "static|dynamic",
            "IsModifiable": "boolean",
            "MinimumEngineVersion": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 3.5 `modify-cluster-parameter-group`

Modifies the parameters of a parameter group.

**Synopsis:**
```bash
aws redshift modify-cluster-parameter-group \
    --parameter-group-name <value> \
    --parameters <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--parameter-group-name` | **Yes** | string | -- | Parameter group to modify |
| `--parameters` | **Yes** | list | -- | Parameters to modify. Shorthand: `ParameterName=string,ParameterValue=string,Description=string,Source=string,DataType=string,AllowedValues=string,ApplyType=static\|dynamic,IsModifiable=boolean ...` |

**Output Schema:**
```json
{
    "ParameterGroupName": "string",
    "ParameterGroupStatus": "string"
}
```

---

### 3.6 `reset-cluster-parameter-group`

Sets one or more parameters of a parameter group to their default values.

**Synopsis:**
```bash
aws redshift reset-cluster-parameter-group \
    --parameter-group-name <value> \
    [--reset-all-parameters | --no-reset-all-parameters] \
    [--parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--parameter-group-name` | **Yes** | string | -- | Parameter group to reset |
| `--reset-all-parameters` | No | boolean | false | Reset all parameters to defaults |
| `--parameters` | No | list | -- | Specific parameters to reset |

**Output Schema:**
```json
{
    "ParameterGroupName": "string",
    "ParameterGroupStatus": "string"
}
```

---

### 3.7 `describe-default-cluster-parameters`

Returns information about the default parameter values for a parameter group family. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-default-cluster-parameters \
    --parameter-group-family <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--parameter-group-family` | **Yes** | string | -- | Parameter group family (e.g., `redshift-1.0`) |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "DefaultClusterParameters": {
        "ParameterGroupFamily": "string",
        "Marker": "string",
        "Parameters": [
            {
                "ParameterName": "string",
                "ParameterValue": "string",
                "Description": "string",
                "Source": "engine-default",
                "DataType": "string",
                "AllowedValues": "string",
                "ApplyType": "static|dynamic",
                "IsModifiable": "boolean",
                "MinimumEngineVersion": "string"
            }
        ]
    }
}
```
