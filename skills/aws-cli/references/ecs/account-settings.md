# Account Settings

### 8.1 `list-account-settings`

Lists the account settings for a specified principal.

**Synopsis:**
```bash
aws ecs list-account-settings \
    [--name <value>] \
    [--value <value>] \
    [--principal-arn <value>] \
    [--effective-settings | --no-effective-settings] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Setting name: `serviceLongArnFormat`, `taskLongArnFormat`, `containerInstanceLongArnFormat`, `awsvpcTrunking`, `containerInsights`, `fargateFIPSMode`, `tagResourceAuthorization`, `fargateTaskRetirementWaitPeriod`, `guardDutyActivate`, `dualStackIPv6` |
| `--value` | No | string | None | Filter by value |
| `--principal-arn` | No | string | None | IAM user/role/root ARN to check settings for |
| `--effective-settings` | No | boolean | false | Return the effective settings (includes defaults) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "settings": [
        {
            "name": "string",
            "value": "string",
            "principalArn": "string",
            "type": "user|aws_managed"
        }
    ],
    "nextToken": "string"
}
```

---

### 8.2 `put-account-setting`

Modifies an account setting for a specified IAM user, IAM role, or the root user.

**Synopsis:**
```bash
aws ecs put-account-setting \
    --name <value> \
    --value <value> \
    [--principal-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Setting name (see `list-account-settings` for valid names) |
| `--value` | **Yes** | string | -- | Setting value (e.g., `enabled`, `disabled`) |
| `--principal-arn` | No | string | caller | IAM user/role/root ARN |

**Output Schema:**
```json
{
    "setting": {
        "name": "string",
        "value": "string",
        "principalArn": "string",
        "type": "user|aws_managed"
    }
}
```

---

### 8.3 `put-account-setting-default`

Modifies an account setting for all IAM users on an account for whom no individual account setting has been specified.

**Synopsis:**
```bash
aws ecs put-account-setting-default \
    --name <value> \
    --value <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Setting name |
| `--value` | **Yes** | string | -- | Setting value |

**Output Schema:**
```json
{
    "setting": {
        "name": "string",
        "value": "string",
        "principalArn": "string",
        "type": "user|aws_managed"
    }
}
```

---

### 8.4 `delete-account-setting`

Deletes a specified account setting for a principal.

**Synopsis:**
```bash
aws ecs delete-account-setting \
    --name <value> \
    [--principal-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Setting name |
| `--principal-arn` | No | string | caller | IAM user/role/root ARN |

**Output Schema:**
```json
{
    "setting": {
        "name": "string",
        "value": "string",
        "principalArn": "string",
        "type": "user|aws_managed"
    }
}
```
