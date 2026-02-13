# Notification Targets

### 6.1 `subscribe`

Subscribes a target to a notification rule.

**Synopsis:**
```bash
aws codestar-notifications subscribe \
    --arn <value> \
    --target <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the notification rule |
| `--target` | **Yes** | structure | -- | Target to subscribe. Shorthand: `TargetType=SNS,TargetAddress=arn:aws:sns:...` |
| `--client-request-token` | No | string | Auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

### 6.2 `unsubscribe`

Unsubscribes a target from a notification rule.

**Synopsis:**
```bash
aws codestar-notifications unsubscribe \
    --arn <value> \
    --target-address <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the notification rule |
| `--target-address` | **Yes** | string | -- | ARN of the target to unsubscribe (e.g., SNS topic ARN) |

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

### 6.3 `list-targets`

Lists notification targets. **Paginated operation.**

**Synopsis:**
```bash
aws codestar-notifications list-targets \
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
| `--filters` | No | list | None | Filters. Shorthand: `Name=TARGET_TYPE\|TARGET_ADDRESS\|TARGET_STATUS,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Targets": [
        {
            "TargetAddress": "string",
            "TargetType": "SNS|AWSChatbotSlack|AWSChatbotMicrosoftTeams",
            "TargetStatus": "PENDING|ACTIVE|UNREACHABLE|INACTIVE|DEACTIVATED"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `delete-target`

Deletes a notification target. Removes the target from all notification rules associated with it.

**Synopsis:**
```bash
aws codestar-notifications delete-target \
    --target-address <value> \
    [--force-unsubscribe-all | --no-force-unsubscribe-all] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-address` | **Yes** | string | -- | ARN of the target to delete |
| `--force-unsubscribe-all` | No | boolean | false | Force unsubscribe the target from all notification rules |

**Output Schema:**
```json
{}
```
