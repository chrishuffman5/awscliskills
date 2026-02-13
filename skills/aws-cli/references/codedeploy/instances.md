# Instances

On-premises instance management for CodeDeploy.

---

### 6.1 `register-on-premises-instance`

Registers an on-premises instance with CodeDeploy.

**Synopsis:**
```bash
aws deploy register-on-premises-instance \
    --instance-name <value> \
    [--iam-session-arn <value>] \
    [--iam-user-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | On-premises instance name |
| `--iam-session-arn` | No | string | None | IAM session ARN (for session-based auth) |
| `--iam-user-arn` | No | string | None | IAM user ARN (for user-based auth) |

> **Note:** You must specify either `--iam-session-arn` or `--iam-user-arn`, but not both.

**Output Schema:**
```json
{}
```

---

### 6.2 `deregister-on-premises-instance`

Deregisters an on-premises instance from CodeDeploy.

**Synopsis:**
```bash
aws deploy deregister-on-premises-instance \
    --instance-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | On-premises instance name |

**Output Schema:**
```json
{}
```

---

### 6.3 `get-on-premises-instance`

Gets information about an on-premises instance.

**Synopsis:**
```bash
aws deploy get-on-premises-instance \
    --instance-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | On-premises instance name |

**Output Schema:**
```json
{
    "instanceInfo": {
        "instanceName": "string",
        "iamSessionArn": "string",
        "iamUserArn": "string",
        "instanceArn": "string",
        "registerTime": "timestamp",
        "deregisterTime": "timestamp",
        "tags": [
            {
                "Key": "string",
                "Value": "string"
            }
        ]
    }
}
```

---

### 6.4 `list-on-premises-instances`

Gets a list of on-premises instance names. **Paginated operation.**

**Synopsis:**
```bash
aws deploy list-on-premises-instances \
    [--registration-status <value>] \
    [--tag-filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-status` | No | string | `Registered` | Registration status: `Registered`, `Deregistered` |
| `--tag-filters` | No | list | None | Tag filters. Shorthand: `Key=string,Value=string,Type=KEY_ONLY\|VALUE_ONLY\|KEY_AND_VALUE ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "instanceNames": ["string"],
    "nextToken": "string"
}
```

---

### 6.5 `batch-get-on-premises-instances`

Gets information about one or more on-premises instances.

**Synopsis:**
```bash
aws deploy batch-get-on-premises-instances \
    --instance-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-names` | **Yes** | list(string) | -- | On-premises instance names |

**Output Schema:**
```json
{
    "instanceInfos": [
        {
            "instanceName": "string",
            "iamSessionArn": "string",
            "iamUserArn": "string",
            "instanceArn": "string",
            "registerTime": "timestamp",
            "deregisterTime": "timestamp",
            "tags": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ]
        }
    ]
}
```

---

### 6.6 `add-tags-to-on-premises-instances`

Adds tags to on-premises instances.

**Synopsis:**
```bash
aws deploy add-tags-to-on-premises-instances \
    --tags <value> \
    --instance-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |
| `--instance-names` | **Yes** | list(string) | -- | On-premises instance names |

**Output Schema:**
```json
{}
```

---

### 6.7 `remove-tags-from-on-premises-instances`

Removes tags from on-premises instances.

**Synopsis:**
```bash
aws deploy remove-tags-from-on-premises-instances \
    --tags <value> \
    --instance-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tags` | **Yes** | list | -- | Tags to remove. Shorthand: `Key=string,Value=string ...` |
| `--instance-names` | **Yes** | list(string) | -- | On-premises instance names |

**Output Schema:**
```json
{}
```
