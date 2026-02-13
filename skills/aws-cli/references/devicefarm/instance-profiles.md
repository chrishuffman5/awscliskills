# Instance Profiles

### 8.1 `create-instance-profile`

Creates an instance profile for managing device configurations.

**Synopsis:**
```bash
aws devicefarm create-instance-profile \
    --name <value> \
    [--description <value>] \
    [--package-cleanup | --no-package-cleanup] \
    [--exclude-app-packages-from-cleanup <value>] \
    [--reboot-after-use | --no-reboot-after-use] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the instance profile |
| `--description` | No | string | None | Description of the instance profile |
| `--package-cleanup` | No | boolean | true | Clean up packages after test run |
| `--exclude-app-packages-from-cleanup` | No | list(string) | None | Package names to exclude from cleanup |
| `--reboot-after-use` | No | boolean | true | Reboot device after use |

**Output Schema:**
```json
{
    "instanceProfile": {
        "arn": "string",
        "packageCleanup": "boolean",
        "excludeAppPackagesFromCleanup": ["string"],
        "rebootAfterUse": "boolean",
        "name": "string",
        "description": "string"
    }
}
```

---

### 8.2 `delete-instance-profile`

Deletes an instance profile.

**Synopsis:**
```bash
aws devicefarm delete-instance-profile \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the instance profile to delete |

**Output Schema:**
```json
{}
```

---

### 8.3 `get-instance-profile`

Returns information about an instance profile.

**Synopsis:**
```bash
aws devicefarm get-instance-profile \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the instance profile |

**Output Schema:**
```json
{
    "instanceProfile": {
        "arn": "string",
        "packageCleanup": "boolean",
        "excludeAppPackagesFromCleanup": ["string"],
        "rebootAfterUse": "boolean",
        "name": "string",
        "description": "string"
    }
}
```

---

### 8.4 `list-instance-profiles`

Returns information about all instance profiles. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-instance-profiles \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "instanceProfiles": [
        {
            "arn": "string",
            "packageCleanup": "boolean",
            "excludeAppPackagesFromCleanup": ["string"],
            "rebootAfterUse": "boolean",
            "name": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 8.5 `update-instance-profile`

Updates an instance profile.

**Synopsis:**
```bash
aws devicefarm update-instance-profile \
    --arn <value> \
    [--name <value>] \
    [--description <value>] \
    [--package-cleanup | --no-package-cleanup] \
    [--exclude-app-packages-from-cleanup <value>] \
    [--reboot-after-use | --no-reboot-after-use] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the instance profile to update |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--package-cleanup` | No | boolean | None | Updated package cleanup setting |
| `--exclude-app-packages-from-cleanup` | No | list(string) | None | Updated exclusion list |
| `--reboot-after-use` | No | boolean | None | Updated reboot setting |

**Output Schema:**
```json
{
    "instanceProfile": {
        "arn": "string",
        "packageCleanup": "boolean",
        "excludeAppPackagesFromCleanup": ["string"],
        "rebootAfterUse": "boolean",
        "name": "string",
        "description": "string"
    }
}
```
