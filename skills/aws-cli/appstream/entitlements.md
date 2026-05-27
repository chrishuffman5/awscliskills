# Entitlements

### 7.1 `create-entitlement`

Creates an entitlement to control access to applications based on user attributes.

**Synopsis:**
```bash
aws appstream create-entitlement \
    --name <value> \
    --stack-name <value> \
    --app-visibility <value> \
    --attributes <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the entitlement |
| `--stack-name` | **Yes** | string | -- | Name of the stack |
| `--app-visibility` | **Yes** | string | -- | Application visibility: `ALL`, `ASSOCIATED` |
| `--attributes` | **Yes** | list | -- | Entitlement attributes. Shorthand: `Name=string,Value=string ...` |
| `--description` | No | string | -- | Description of the entitlement |

**Output Schema:**
```json
{
    "Entitlement": {
        "Name": "string",
        "StackName": "string",
        "Description": "string",
        "AppVisibility": "ALL|ASSOCIATED",
        "Attributes": [
            {
                "Name": "string",
                "Value": "string"
            }
        ],
        "CreatedTime": "timestamp",
        "LastModifiedTime": "timestamp"
    }
}
```

---

### 7.2 `delete-entitlement`

Deletes the specified entitlement.

**Synopsis:**
```bash
aws appstream delete-entitlement \
    --name <value> \
    --stack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the entitlement |
| `--stack-name` | **Yes** | string | -- | Name of the stack |

**Output Schema:**
```json
{}
```

---

### 7.3 `describe-entitlements`

Describes entitlements for the specified stack.

**Synopsis:**
```bash
aws appstream describe-entitlements \
    --stack-name <value> \
    [--name <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Name of the stack |
| `--name` | No | string | -- | Name of the entitlement to describe |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum number of results |

**Output Schema:**
```json
{
    "Entitlements": [
        {
            "Name": "string",
            "StackName": "string",
            "Description": "string",
            "AppVisibility": "ALL|ASSOCIATED",
            "Attributes": [
                {
                    "Name": "string",
                    "Value": "string"
                }
            ],
            "CreatedTime": "timestamp",
            "LastModifiedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.4 `update-entitlement`

Updates the specified entitlement.

**Synopsis:**
```bash
aws appstream update-entitlement \
    --name <value> \
    --stack-name <value> \
    [--description <value>] \
    [--app-visibility <value>] \
    [--attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the entitlement |
| `--stack-name` | **Yes** | string | -- | Name of the stack |
| `--description` | No | string | -- | Description |
| `--app-visibility` | No | string | -- | Application visibility: `ALL`, `ASSOCIATED` |
| `--attributes` | No | list | -- | Entitlement attributes |

**Output Schema:**
```json
{
    "Entitlement": {
        "Name": "string",
        "StackName": "string",
        "Description": "string",
        "AppVisibility": "ALL|ASSOCIATED",
        "Attributes": [
            {
                "Name": "string",
                "Value": "string"
            }
        ],
        "CreatedTime": "timestamp",
        "LastModifiedTime": "timestamp"
    }
}
```

---

### 7.5 `list-entitled-applications`

Lists the applications entitled to the specified stack and entitlement.

**Synopsis:**
```bash
aws appstream list-entitled-applications \
    --stack-name <value> \
    --entitlement-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Name of the stack |
| `--entitlement-name` | **Yes** | string | -- | Name of the entitlement |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum number of results |

**Output Schema:**
```json
{
    "EntitledApplications": [
        {
            "ApplicationIdentifier": "string"
        }
    ],
    "NextToken": "string"
}
```
