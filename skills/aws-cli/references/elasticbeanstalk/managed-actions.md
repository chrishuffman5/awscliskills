# Managed Actions

Managed actions are platform updates and maintenance operations that Elastic Beanstalk schedules for your environments when managed platform updates are enabled.

### 4.1 `describe-environment-managed-actions`

Lists the pending and in-progress managed actions for an environment.

**Synopsis:**
```bash
aws elasticbeanstalk describe-environment-managed-actions \
    [--environment-name <value>] \
    [--environment-id <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-name` | No | string | -- | Environment name |
| `--environment-id` | No | string | -- | Environment ID |
| `--status` | No | string | -- | Filter by status: `Scheduled`, `Pending`, `Running`, `Unknown` |

**Output Schema:**
```json
{
    "ManagedActions": [
        {
            "ActionId": "string",
            "ActionDescription": "string",
            "ActionType": "InstanceRefresh|PlatformUpdate|Unknown",
            "Status": "Scheduled|Pending|Running|Unknown",
            "WindowStartTime": "timestamp"
        }
    ]
}
```

---

### 4.2 `describe-environment-managed-action-history`

Lists completed and failed managed actions for an environment. **Paginated operation.**

**Synopsis:**
```bash
aws elasticbeanstalk describe-environment-managed-action-history \
    [--environment-id <value>] \
    [--environment-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | No | string | -- | Environment ID |
| `--environment-name` | No | string | -- | Environment name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ManagedActionHistoryItems": [
        {
            "ActionId": "string",
            "ActionType": "InstanceRefresh|PlatformUpdate|Unknown",
            "ActionDescription": "string",
            "FailureType": "UpdateCancelled|CancellationFailed|RollbackFailed|RollbackSuccessful|InternalFailure|InvalidEnvironmentState|PermissionsError",
            "Status": "Completed|Failed|Unknown",
            "FailureDescription": "string",
            "ExecutedTime": "timestamp",
            "FinishedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.3 `apply-environment-managed-action`

Applies a scheduled managed action immediately. A managed action can be applied only if its status is `Scheduled`.

**Synopsis:**
```bash
aws elasticbeanstalk apply-environment-managed-action \
    --action-id <value> \
    [--environment-name <value>] \
    [--environment-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-id` | **Yes** | string | -- | ID of the managed action to apply |
| `--environment-name` | No | string | -- | Environment name |
| `--environment-id` | No | string | -- | Environment ID |

**Output Schema:**
```json
{
    "ActionId": "string",
    "ActionDescription": "string",
    "ActionType": "InstanceRefresh|PlatformUpdate|Unknown",
    "Status": "string"
}
```
