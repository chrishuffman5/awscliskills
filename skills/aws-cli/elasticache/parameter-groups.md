# Parameter Groups

### 3.1 `create-cache-parameter-group`

Creates a new cache parameter group. A parameter group is a collection of parameters applied to all nodes in a cluster.

**Synopsis:**
```bash
aws elasticache create-cache-parameter-group \
    --cache-parameter-group-name <value> \
    --cache-parameter-group-family <value> \
    --description <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-parameter-group-name` | **Yes** | string | -- | Name for the parameter group |
| `--cache-parameter-group-family` | **Yes** | string | -- | Family: `redis7`, `redis6.x`, `redis5.0`, `valkey8`, `valkey7`, `memcached1.6`, etc. |
| `--description` | **Yes** | string | -- | Description of the parameter group |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "CacheParameterGroup": {
        "CacheParameterGroupName": "string",
        "CacheParameterGroupFamily": "string",
        "Description": "string",
        "IsGlobal": "boolean",
        "ARN": "string"
    }
}
```

---

### 3.2 `delete-cache-parameter-group`

Deletes a cache parameter group. Cannot delete a group that is associated with any cache clusters or used as a default.

**Synopsis:**
```bash
aws elasticache delete-cache-parameter-group \
    --cache-parameter-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-parameter-group-name` | **Yes** | string | -- | Name of the parameter group to delete |

**Output:** None on success.

---

### 3.3 `describe-cache-parameter-groups`

Returns a list of cache parameter group descriptions. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-cache-parameter-groups \
    [--cache-parameter-group-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-parameter-group-name` | No | string | -- | Specific parameter group name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CacheParameterGroups": [
        {
            "CacheParameterGroupName": "string",
            "CacheParameterGroupFamily": "string",
            "Description": "string",
            "IsGlobal": "boolean",
            "ARN": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `describe-cache-parameters`

Returns the detailed parameter list for a particular cache parameter group. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-cache-parameters \
    --cache-parameter-group-name <value> \
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
| `--cache-parameter-group-name` | **Yes** | string | -- | Name of the parameter group |
| `--source` | No | string | -- | Filter by source: `user`, `system`, or `engine-default` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
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
            "DataType": "string",
            "AllowedValues": "string",
            "IsModifiable": "boolean",
            "MinimumEngineVersion": "string",
            "ChangeType": "immediate|requires-reboot"
        }
    ],
    "CacheNodeTypeSpecificParameters": [
        {
            "ParameterName": "string",
            "Description": "string",
            "Source": "string",
            "DataType": "string",
            "AllowedValues": "string",
            "IsModifiable": "boolean",
            "MinimumEngineVersion": "string",
            "CacheNodeTypeSpecificValues": [
                {
                    "CacheNodeType": "string",
                    "Value": "string"
                }
            ],
            "ChangeType": "immediate|requires-reboot"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `modify-cache-parameter-group`

Modifies the parameters of a cache parameter group.

**Synopsis:**
```bash
aws elasticache modify-cache-parameter-group \
    --cache-parameter-group-name <value> \
    --parameter-name-values <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-parameter-group-name` | **Yes** | string | -- | Name of the parameter group |
| `--parameter-name-values` | **Yes** | list | -- | Parameters to modify. Shorthand: `ParameterName=string,ParameterValue=string ...` |

**Output Schema:**
```json
{
    "CacheParameterGroupName": "string"
}
```

---

### 3.6 `reset-cache-parameter-group`

Resets parameters in a cache parameter group to their default values.

**Synopsis:**
```bash
aws elasticache reset-cache-parameter-group \
    --cache-parameter-group-name <value> \
    [--reset-all-parameters | --no-reset-all-parameters] \
    [--parameter-name-values <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-parameter-group-name` | **Yes** | string | -- | Name of the parameter group |
| `--reset-all-parameters` | No | boolean | false | Reset all parameters to defaults |
| `--parameter-name-values` | No | list | -- | Specific parameters to reset. Shorthand: `ParameterName=string,ParameterValue=string ...` |

**Output Schema:**
```json
{
    "CacheParameterGroupName": "string"
}
```

---

### 3.7 `describe-engine-default-parameters`

Returns the default engine and system parameter information for the specified cache engine. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-engine-default-parameters \
    --cache-parameter-group-family <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-parameter-group-family` | **Yes** | string | -- | Parameter group family (e.g., `redis7`, `memcached1.6`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "EngineDefaults": {
        "CacheParameterGroupFamily": "string",
        "Marker": "string",
        "Parameters": [
            {
                "ParameterName": "string",
                "ParameterValue": "string",
                "Description": "string",
                "Source": "string",
                "DataType": "string",
                "AllowedValues": "string",
                "IsModifiable": "boolean",
                "MinimumEngineVersion": "string",
                "ChangeType": "immediate|requires-reboot"
            }
        ],
        "CacheNodeTypeSpecificParameters": []
    }
}
```
