# Action Connectors

Action connectors enable triggering external actions from QuickSight dashboards (e.g., sending notifications, invoking workflows).

### 18.1 `create-action-connector`

Creates an action connector.

**Synopsis:**
```bash
aws quicksight create-action-connector \
    --aws-account-id <value> \
    --action-connector-id <value> \
    --name <value> \
    --connector-definition <value> \
    [--permissions <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--action-connector-id` | **Yes** | string | -- | Connector ID |
| `--name` | **Yes** | string | -- | Display name |
| `--connector-definition` | **Yes** | structure | -- | Connector definition |
| `--permissions` | No | list | None | Resource permissions |
| `--tags` | No | list | None | Resource tags |

**Output Schema:**
```json
{
    "Arn": "string",
    "ActionConnectorId": "string",
    "CreationStatus": "string",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 18.2 `describe-action-connector` / `update-action-connector` / `delete-action-connector`

Manage action connectors.

**Synopsis:**
```bash
aws quicksight describe-action-connector --aws-account-id <value> --action-connector-id <value>
aws quicksight update-action-connector --aws-account-id <value> --action-connector-id <value> --name <value> --connector-definition <value>
aws quicksight delete-action-connector --aws-account-id <value> --action-connector-id <value>
```

---

### 18.3 `list-action-connectors` / `search-action-connectors`

List or search action connectors.

**Synopsis:**
```bash
aws quicksight list-action-connectors --aws-account-id <value>
aws quicksight search-action-connectors --aws-account-id <value> --filters <value>
```

---

### 18.4 `describe-action-connector-permissions` / `update-action-connector-permissions`

Manage action connector permissions.

**Synopsis:**
```bash
aws quicksight describe-action-connector-permissions --aws-account-id <value> --action-connector-id <value>
aws quicksight update-action-connector-permissions --aws-account-id <value> --action-connector-id <value> \
    [--grant-permissions <value>] [--revoke-permissions <value>]
```
