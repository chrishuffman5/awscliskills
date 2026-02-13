# Control Panels

Commands for managing Route 53 ARC control panels via `aws route53-recovery-control-config`.

### 3.1 `create-control-panel`

Creates a control panel in the specified cluster. A control panel is a group of routing controls.

**Synopsis:**
```bash
aws route53-recovery-control-config create-control-panel \
    --cluster-arn <value> \
    --control-panel-name <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster (1-256 chars) |
| `--control-panel-name` | **Yes** | string | -- | Name of the control panel (1-64 chars) |
| `--client-token` | No | string | None | Idempotency token (1-64 chars) |
| `--tags` | No | map | None | Tags as key-value pairs |

**Output Schema:**
```json
{
    "ControlPanel": {
        "ClusterArn": "string",
        "ControlPanelArn": "string",
        "DefaultControlPanel": false,
        "Name": "string",
        "RoutingControlCount": "integer",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "Owner": "string"
    }
}
```

---

### 3.2 `delete-control-panel`

Deletes a control panel. All routing controls in the panel must be deleted first.

**Synopsis:**
```bash
aws route53-recovery-control-config delete-control-panel \
    --control-panel-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-panel-arn` | **Yes** | string | -- | ARN of the control panel to delete |

**Output:** None on success.

---

### 3.3 `describe-control-panel`

Gets details about a control panel.

**Synopsis:**
```bash
aws route53-recovery-control-config describe-control-panel \
    --control-panel-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-panel-arn` | **Yes** | string | -- | ARN of the control panel |

**Output Schema:**
```json
{
    "ControlPanel": {
        "ClusterArn": "string",
        "ControlPanelArn": "string",
        "DefaultControlPanel": "boolean",
        "Name": "string",
        "RoutingControlCount": "integer",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "Owner": "string"
    }
}
```

---

### 3.4 `update-control-panel`

Updates a control panel name.

**Synopsis:**
```bash
aws route53-recovery-control-config update-control-panel \
    --control-panel-arn <value> \
    --control-panel-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-panel-arn` | **Yes** | string | -- | ARN of the control panel |
| `--control-panel-name` | **Yes** | string | -- | New name for the control panel (1-64 chars) |

**Output Schema:**
```json
{
    "ControlPanel": {
        "ClusterArn": "string",
        "ControlPanelArn": "string",
        "DefaultControlPanel": "boolean",
        "Name": "string",
        "RoutingControlCount": "integer",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "Owner": "string"
    }
}
```

---

### 3.5 `list-control-panels`

Lists control panels. Optionally filter by cluster. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-control-config list-control-panels \
    [--cluster-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | No | string | None | ARN of a cluster to filter by |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ControlPanels": [
        {
            "ClusterArn": "string",
            "ControlPanelArn": "string",
            "DefaultControlPanel": "boolean",
            "Name": "string",
            "RoutingControlCount": "integer",
            "Status": "PENDING|DEPLOYED|PENDING_DELETION",
            "Owner": "string"
        }
    ],
    "NextToken": "string"
}
```
