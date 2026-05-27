# Extensions

### 7.1 `create-extension`

Creates an extension. An extension augments an AppConfig workflow by invoking actions at specific action points during the deployment lifecycle.

**Synopsis:**
```bash
aws appconfig create-extension \
    --name <value> \
    --actions <value> \
    [--description <value>] \
    [--parameters <value>] \
    [--tags <value>] \
    [--latest-version-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Extension name (1-64 chars) |
| `--actions` | **Yes** | map | -- | Actions defined in the extension (1-5 action points) |
| `--description` | No | string | None | Description (0-1024 chars) |
| `--parameters` | No | map | None | Parameters accepted by the extension (1-10) |
| `--tags` | No | map | None | Tags (max 50) |
| `--latest-version-number` | No | integer | None | Specify current version number when creating a new version |

**Action Points:**
`PRE_CREATE_HOSTED_CONFIGURATION_VERSION`, `PRE_START_DEPLOYMENT`, `AT_DEPLOYMENT_TICK`, `ON_DEPLOYMENT_START`, `ON_DEPLOYMENT_STEP`, `ON_DEPLOYMENT_BAKING`, `ON_DEPLOYMENT_COMPLETE`, `ON_DEPLOYMENT_ROLLED_BACK`

**Actions structure:**
```json
{
    "PRE_START_DEPLOYMENT": [
        {
            "Name": "string",
            "Description": "string",
            "Uri": "string",
            "RoleArn": "string"
        }
    ]
}
```

**Parameters structure:**
```json
{
    "ParameterName": {
        "Description": "string",
        "Required": true,
        "Dynamic": false
    }
}
```

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "VersionNumber": "integer",
    "Arn": "string",
    "Description": "string",
    "Actions": {},
    "Parameters": {}
}
```

---

### 7.2 `get-extension`

Retrieves extension details.

**Synopsis:**
```bash
aws appconfig get-extension \
    --extension-identifier <value> \
    [--version-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--extension-identifier` | **Yes** | string | -- | Extension name, ID, or ARN (1-2048 chars) |
| `--version-number` | No | integer | None | Specific version number |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "VersionNumber": "integer",
    "Arn": "string",
    "Description": "string",
    "Actions": {},
    "Parameters": {}
}
```

---

### 7.3 `list-extensions`

Lists all extensions. **Paginated operation.**

**Synopsis:**
```bash
aws appconfig list-extensions \
    [--max-results <value>] \
    [--next-token <value>] \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |
| `--name` | No | string | None | Filter by extension name |

**Output Schema:**
```json
{
    "Items": [
        {
            "Id": "string",
            "Name": "string",
            "VersionNumber": "integer",
            "Arn": "string",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.4 `update-extension`

Updates an extension. Creating a new version increments the version number.

**Synopsis:**
```bash
aws appconfig update-extension \
    --extension-identifier <value> \
    [--description <value>] \
    [--actions <value>] \
    [--parameters <value>] \
    [--version-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--extension-identifier` | **Yes** | string | -- | Extension name, ID, or ARN |
| `--description` | No | string | None | Updated description |
| `--actions` | No | map | None | Updated actions |
| `--parameters` | No | map | None | Updated parameters |
| `--version-number` | No | integer | None | Current version number for updating |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "VersionNumber": "integer",
    "Arn": "string",
    "Description": "string",
    "Actions": {},
    "Parameters": {}
}
```

---

### 7.5 `delete-extension`

Deletes an extension.

**Synopsis:**
```bash
aws appconfig delete-extension \
    --extension-identifier <value> \
    [--version-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--extension-identifier` | **Yes** | string | -- | Extension name, ID, or ARN |
| `--version-number` | No | integer | None | Version number to delete |

**Output:** None

---

### 7.6 `create-extension-association`

Associates an extension with an AppConfig resource (application, configuration profile, or environment).

**Synopsis:**
```bash
aws appconfig create-extension-association \
    --extension-identifier <value> \
    --resource-identifier <value> \
    [--extension-version-number <value>] \
    [--parameters <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--extension-identifier` | **Yes** | string | -- | Extension name, ID, or ARN (1-2048 chars) |
| `--resource-identifier` | **Yes** | string | -- | ARN of the application, configuration profile, or environment (1-2048 chars) |
| `--extension-version-number` | No | integer | Max version | Extension version number |
| `--parameters` | No | map | None | Parameter values (0-10) |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "Id": "string",
    "ExtensionArn": "string",
    "ResourceArn": "string",
    "Arn": "string",
    "Parameters": {},
    "ExtensionVersionNumber": "integer"
}
```

---

### 7.7 `get-extension-association`

Retrieves extension association details.

**Synopsis:**
```bash
aws appconfig get-extension-association \
    --extension-association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--extension-association-id` | **Yes** | string | -- | Association ID |

**Output Schema:**
```json
{
    "Id": "string",
    "ExtensionArn": "string",
    "ResourceArn": "string",
    "Arn": "string",
    "Parameters": {},
    "ExtensionVersionNumber": "integer"
}
```

---

### 7.8 `list-extension-associations`

Lists extension associations. **Paginated operation.**

**Synopsis:**
```bash
aws appconfig list-extension-associations \
    [--resource-identifier <value>] \
    [--extension-identifier <value>] \
    [--extension-version-number <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-identifier` | No | string | None | Filter by resource ARN |
| `--extension-identifier` | No | string | None | Filter by extension name, ID, or ARN |
| `--extension-version-number` | No | integer | None | Filter by extension version |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Items": [
        {
            "Id": "string",
            "ExtensionArn": "string",
            "ResourceArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.9 `update-extension-association`

Updates an extension association.

**Synopsis:**
```bash
aws appconfig update-extension-association \
    --extension-association-id <value> \
    [--parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--extension-association-id` | **Yes** | string | -- | Association ID |
| `--parameters` | No | map | None | Updated parameter values |

**Output Schema:**
```json
{
    "Id": "string",
    "ExtensionArn": "string",
    "ResourceArn": "string",
    "Arn": "string",
    "Parameters": {},
    "ExtensionVersionNumber": "integer"
}
```

---

### 7.10 `delete-extension-association`

Deletes an extension association.

**Synopsis:**
```bash
aws appconfig delete-extension-association \
    --extension-association-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--extension-association-id` | **Yes** | string | -- | Association ID to delete |

**Output:** None
