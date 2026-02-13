# Organizational Units

### 3.1 `create-organizational-unit`

Creates an organizational unit (OU) within a root or parent OU.

**Synopsis:**
```bash
aws organizations create-organizational-unit \
    --parent-id <value> \
    --name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--parent-id` | **Yes** | string | -- | Parent root ID (`r-`) or OU ID (`ou-`) |
| `--name` | **Yes** | string | -- | Friendly name for the OU |
| `--tags` | No | list | None | Tags for the OU. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "OrganizationalUnit": {
        "Id": "string",
        "Arn": "string",
        "Name": "string"
    }
}
```

---

### 3.2 `delete-organizational-unit`

Deletes an OU. The OU must be empty (no accounts or child OUs).

**Synopsis:**
```bash
aws organizations delete-organizational-unit \
    --organizational-unit-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organizational-unit-id` | **Yes** | string | -- | ID of the OU to delete |

**Output Schema:**
```json
{}
```

---

### 3.3 `describe-organizational-unit`

Retrieves information about an organizational unit.

**Synopsis:**
```bash
aws organizations describe-organizational-unit \
    --organizational-unit-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organizational-unit-id` | **Yes** | string | -- | ID of the OU |

**Output Schema:**
```json
{
    "OrganizationalUnit": {
        "Id": "string",
        "Arn": "string",
        "Name": "string"
    }
}
```

---

### 3.4 `list-organizational-units-for-parent`

Lists the OUs that are direct children of a specified parent (root or OU). **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-organizational-units-for-parent \
    --parent-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--parent-id` | **Yes** | string | -- | Root ID or OU ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OrganizationalUnits": [
        {
            "Id": "string",
            "Arn": "string",
            "Name": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `list-children`

Lists the children (accounts and OUs) of a specified parent. **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-children \
    --parent-id <value> \
    --child-type <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--parent-id` | **Yes** | string | -- | Root ID or OU ID |
| `--child-type` | **Yes** | string | -- | Type of children: `ACCOUNT` or `ORGANIZATIONAL_UNIT` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Children": [
        {
            "Id": "string",
            "Type": "ACCOUNT|ORGANIZATIONAL_UNIT"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.6 `list-parents`

Lists the root or OUs that serve as the immediate parent of the specified child.

**Synopsis:**
```bash
aws organizations list-parents \
    --child-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--child-id` | **Yes** | string | -- | Account ID or OU ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Parents": [
        {
            "Id": "string",
            "Type": "ROOT|ORGANIZATIONAL_UNIT"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.7 `update-organizational-unit`

Renames an organizational unit.

**Synopsis:**
```bash
aws organizations update-organizational-unit \
    --organizational-unit-id <value> \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organizational-unit-id` | **Yes** | string | -- | ID of the OU to rename |
| `--name` | No | string | None | New name for the OU |

**Output Schema:**
```json
{
    "OrganizationalUnit": {
        "Id": "string",
        "Arn": "string",
        "Name": "string"
    }
}
```
