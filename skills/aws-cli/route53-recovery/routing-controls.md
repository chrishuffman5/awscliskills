# Routing Controls

## Data Plane Commands (route53-recovery-cluster)

### 1.1 `get-routing-control-state`

Gets the current state (On/Off) of a routing control. Must use a Regional cluster endpoint.

**Synopsis:**
```bash
aws route53-recovery-cluster get-routing-control-state \
    --routing-control-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--routing-control-arn` | **Yes** | string | -- | ARN of the routing control (1-255 chars) |

**Output Schema:**
```json
{
    "RoutingControlArn": "string",
    "RoutingControlState": "On|Off",
    "RoutingControlName": "string"
}
```

---

### 1.2 `list-routing-controls` (data plane)

Lists routing controls in a cluster. Optionally filter by control panel. Must use a Regional cluster endpoint. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-cluster list-routing-controls \
    [--control-panel-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-panel-arn` | No | string | None | ARN of a control panel to filter by |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RoutingControls": [
        {
            "ControlPanelArn": "string",
            "ControlPanelName": "string",
            "RoutingControlArn": "string",
            "RoutingControlName": "string",
            "RoutingControlState": "On|Off",
            "Owner": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.3 `update-routing-control-state`

Updates the state of a single routing control to On or Off. Supports safety rule overrides for break-glass scenarios. Must use a Regional cluster endpoint.

**Synopsis:**
```bash
aws route53-recovery-cluster update-routing-control-state \
    --routing-control-arn <value> \
    --routing-control-state <value> \
    [--safety-rules-to-override <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--routing-control-arn` | **Yes** | string | -- | ARN of the routing control to update |
| `--routing-control-state` | **Yes** | string | -- | Target state: `On` or `Off` |
| `--safety-rules-to-override` | No | list(string) | None | ARNs of safety rules to override |

**Output:** None on success.

---

### 1.4 `update-routing-control-states`

Updates the state of multiple routing controls in a single batch operation. Supports safety rule overrides. Must use a Regional cluster endpoint.

**Synopsis:**
```bash
aws route53-recovery-cluster update-routing-control-states \
    --update-routing-control-state-entries <value> \
    [--safety-rules-to-override <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--update-routing-control-state-entries` | **Yes** | list | -- | List of routing control state entries |
| `--safety-rules-to-override` | No | list(string) | None | ARNs of safety rules to override |

**Entry Structure (shorthand):**
```
RoutingControlArn=string,RoutingControlState=string ...
```

**Entry Structure (JSON):**
```json
[
    {
        "RoutingControlArn": "string",
        "RoutingControlState": "On|Off"
    }
]
```

**Output:** None on success.

---

## Control Plane Commands (route53-recovery-control-config)

### 1.5 `create-routing-control`

Creates a routing control in the specified cluster and optionally in a control panel.

**Synopsis:**
```bash
aws route53-recovery-control-config create-routing-control \
    --cluster-arn <value> \
    --routing-control-name <value> \
    [--control-panel-arn <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster (1-256 chars) |
| `--routing-control-name` | **Yes** | string | -- | Name of the routing control (1-64 chars) |
| `--control-panel-arn` | No | string | None | ARN of the control panel. If omitted, uses the cluster default panel |
| `--client-token` | No | string | None | Idempotency token (1-64 chars) |

**Output Schema:**
```json
{
    "RoutingControl": {
        "ControlPanelArn": "string",
        "Name": "string",
        "RoutingControlArn": "string",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "Owner": "string"
    }
}
```

---

### 1.6 `delete-routing-control`

Deletes a routing control.

**Synopsis:**
```bash
aws route53-recovery-control-config delete-routing-control \
    --routing-control-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--routing-control-arn` | **Yes** | string | -- | ARN of the routing control to delete |

**Output:** None on success.

---

### 1.7 `describe-routing-control`

Gets details about a routing control.

**Synopsis:**
```bash
aws route53-recovery-control-config describe-routing-control \
    --routing-control-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--routing-control-arn` | **Yes** | string | -- | ARN of the routing control |

**Output Schema:**
```json
{
    "RoutingControl": {
        "ControlPanelArn": "string",
        "Name": "string",
        "RoutingControlArn": "string",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "Owner": "string"
    }
}
```

---

### 1.8 `update-routing-control`

Updates a routing control name.

**Synopsis:**
```bash
aws route53-recovery-control-config update-routing-control \
    --routing-control-arn <value> \
    --routing-control-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--routing-control-arn` | **Yes** | string | -- | ARN of the routing control |
| `--routing-control-name` | **Yes** | string | -- | New name for the routing control (1-64 chars) |

**Output Schema:**
```json
{
    "RoutingControl": {
        "ControlPanelArn": "string",
        "Name": "string",
        "RoutingControlArn": "string",
        "Status": "PENDING|DEPLOYED|PENDING_DELETION",
        "Owner": "string"
    }
}
```

---

### 1.9 `list-routing-controls` (control plane)

Lists routing controls for a control panel. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-control-config list-routing-controls \
    --control-panel-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--control-panel-arn` | **Yes** | string | -- | ARN of the control panel |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RoutingControls": [
        {
            "ControlPanelArn": "string",
            "Name": "string",
            "RoutingControlArn": "string",
            "Status": "PENDING|DEPLOYED|PENDING_DELETION",
            "Owner": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.10 `list-associated-route53-health-checks`

Lists the Route 53 health checks associated with a routing control. **Paginated operation.**

**Synopsis:**
```bash
aws route53-recovery-control-config list-associated-route53-health-checks \
    --routing-control-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--routing-control-arn` | **Yes** | string | -- | ARN of the routing control |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "HealthCheckIds": ["string"],
    "NextToken": "string"
}
```
