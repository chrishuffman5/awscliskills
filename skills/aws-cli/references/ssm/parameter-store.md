# Parameter Store

### 1.1 `put-parameter`

Creates or updates a parameter in Parameter Store. Supports String, StringList, and SecureString types.

**Synopsis:**
```bash
aws ssm put-parameter \
    --name <value> \
    --value <value> \
    [--description <value>] \
    [--type <value>] \
    [--key-id <value>] \
    [--overwrite | --no-overwrite] \
    [--allowed-pattern <value>] \
    [--tags <value>] \
    [--tier <value>] \
    [--policies <value>] \
    [--data-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Fully qualified parameter name (hierarchical path allowed, e.g. `/app/db/host`) |
| `--value` | **Yes** | string | -- | Parameter value (max 4KB standard, 8KB advanced) |
| `--description` | No | string | None | Description of the parameter (max 1024 chars) |
| `--type` | No | string | -- | Parameter type: `String`, `StringList`, or `SecureString`. Required on create |
| `--key-id` | No | string | default KMS key | KMS key ID or alias for SecureString encryption |
| `--overwrite` | No | boolean | false | Allow overwriting an existing parameter |
| `--allowed-pattern` | No | string | None | Regex pattern to validate parameter value |
| `--tags` | No | list | None | Tags to apply. Shorthand: `Key=string,Value=string ...` |
| `--tier` | No | string | `Standard` | Parameter tier: `Standard`, `Advanced`, or `Intelligent-Tiering` |
| `--policies` | No | string | None | JSON string of parameter policies (expiration, notification) |
| `--data-type` | No | string | `text` | Data type: `text`, `aws:ec2:image`, or `aws:ssm:integration` |

**Output Schema:**
```json
{
    "Version": "long",
    "Tier": "Standard|Advanced|Intelligent-Tiering"
}
```

---

### 1.2 `get-parameter`

Gets the value of a single parameter. Use `--with-decryption` for SecureString parameters.

**Synopsis:**
```bash
aws ssm get-parameter \
    --name <value> \
    [--with-decryption | --no-with-decryption] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Parameter name (supports version `:N` and label `:label` suffixes) |
| `--with-decryption` | No | boolean | false | Decrypt SecureString values |

**Output Schema:**
```json
{
    "Parameter": {
        "Name": "string",
        "Type": "String|StringList|SecureString",
        "Value": "string",
        "Version": "long",
        "Selector": "string",
        "SourceResult": "string",
        "LastModifiedDate": "timestamp",
        "ARN": "string",
        "DataType": "string"
    }
}
```

---

### 1.3 `get-parameters`

Gets the values of one or more parameters. Returns an `InvalidParameters` list for any names that could not be found.

**Synopsis:**
```bash
aws ssm get-parameters \
    --names <value> \
    [--with-decryption | --no-with-decryption] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | **Yes** | list(string) | -- | Parameter names (max 10) |
| `--with-decryption` | No | boolean | false | Decrypt SecureString values |

**Output Schema:**
```json
{
    "Parameters": [
        {
            "Name": "string",
            "Type": "String|StringList|SecureString",
            "Value": "string",
            "Version": "long",
            "LastModifiedDate": "timestamp",
            "ARN": "string",
            "DataType": "string"
        }
    ],
    "InvalidParameters": ["string"]
}
```

---

### 1.4 `get-parameters-by-path`

Retrieves all parameters under a hierarchical path. **Paginated operation.**

**Synopsis:**
```bash
aws ssm get-parameters-by-path \
    --path <value> \
    [--recursive | --no-recursive] \
    [--parameter-filters <value>] \
    [--with-decryption | --no-with-decryption] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--path` | **Yes** | string | -- | Parameter path hierarchy (e.g. `/app/`) |
| `--recursive` | No | boolean | false | Retrieve all parameters under the path recursively |
| `--parameter-filters` | No | list | None | Filters for results |
| `--with-decryption` | No | boolean | false | Decrypt SecureString values |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 10) |
| `--max-items` | No | integer | None | Total items to return |

**Parameter Filter Structure:**
```json
[
    {
        "Key": "Type|KeyId|Path|Label|DataType",
        "Option": "Equals|Contains|BeginsWith|OneLevel|Recursive",
        "Values": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "Parameters": [
        {
            "Name": "string",
            "Type": "String|StringList|SecureString",
            "Value": "string",
            "Version": "long",
            "LastModifiedDate": "timestamp",
            "ARN": "string",
            "DataType": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `delete-parameter`

Deletes a single parameter from Parameter Store.

**Synopsis:**
```bash
aws ssm delete-parameter \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Parameter name to delete |

**Output Schema:**
```json
{}
```

---

### 1.6 `delete-parameters`

Deletes multiple parameters in a single call. Returns lists of deleted and invalid parameter names.

**Synopsis:**
```bash
aws ssm delete-parameters \
    --names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | **Yes** | list(string) | -- | Parameter names to delete (max 10) |

**Output Schema:**
```json
{
    "DeletedParameters": ["string"],
    "InvalidParameters": ["string"]
}
```

---

### 1.7 `describe-parameters`

Lists parameter metadata. Supports filtering by name, type, path, and other attributes. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-parameters \
    [--filters <value>] \
    [--parameter-filters <value>] \
    [--shared | --no-shared] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Legacy filters. Shorthand: `Key=Name\|Type\|KeyId,Values=string ...` |
| `--parameter-filters` | No | list | None | Parameter filters (newer API) |
| `--shared` | No | boolean | false | List shared parameters from other accounts |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 50) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Parameters": [
        {
            "Name": "string",
            "ARN": "string",
            "Type": "String|StringList|SecureString",
            "KeyId": "string",
            "LastModifiedDate": "timestamp",
            "LastModifiedUser": "string",
            "Description": "string",
            "AllowedPattern": "string",
            "Version": "long",
            "Tier": "Standard|Advanced|Intelligent-Tiering",
            "Policies": [
                {
                    "PolicyText": "string",
                    "PolicyType": "string",
                    "PolicyStatus": "string"
                }
            ],
            "DataType": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.8 `get-parameter-history`

Retrieves the history of changes to a parameter, including all versions. **Paginated operation.**

**Synopsis:**
```bash
aws ssm get-parameter-history \
    --name <value> \
    [--with-decryption | --no-with-decryption] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Parameter name |
| `--with-decryption` | No | boolean | false | Decrypt SecureString values |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 50) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Parameters": [
        {
            "Name": "string",
            "Type": "String|StringList|SecureString",
            "KeyId": "string",
            "LastModifiedDate": "timestamp",
            "LastModifiedUser": "string",
            "Description": "string",
            "Value": "string",
            "AllowedPattern": "string",
            "Version": "long",
            "Labels": ["string"],
            "Tier": "Standard|Advanced|Intelligent-Tiering",
            "Policies": [],
            "DataType": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.9 `label-parameter-version`

Attaches one or more labels to a specific version of a parameter. Labels provide an alias for parameter versions.

**Synopsis:**
```bash
aws ssm label-parameter-version \
    --name <value> \
    [--parameter-version <value>] \
    --labels <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Parameter name |
| `--parameter-version` | No | long | latest | Version number to label |
| `--labels` | **Yes** | list(string) | -- | Labels to attach (max 10 per version) |

**Output Schema:**
```json
{
    "InvalidLabels": ["string"],
    "ParameterVersion": "long"
}
```

---

### 1.10 `unlabel-parameter-version`

Removes one or more labels from a parameter version.

**Synopsis:**
```bash
aws ssm unlabel-parameter-version \
    --name <value> \
    --parameter-version <value> \
    --labels <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Parameter name |
| `--parameter-version` | **Yes** | long | -- | Version number to unlabel |
| `--labels` | **Yes** | list(string) | -- | Labels to remove |

**Output Schema:**
```json
{
    "RemovedLabels": ["string"],
    "InvalidLabels": ["string"]
}
```
