# Monitors

### 1.1 `create-monitor`

Creates a monitor between a source subnet and destination IP address. You can also create a monitor with probes using this command. For each monitor, CloudWatch Network Monitor publishes metrics about network connectivity to CloudWatch.

**Synopsis:**
```bash
aws networkmonitor create-monitor \
    --monitor-name <value> \
    [--probes <value>] \
    [--aggregation-period <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name (1-200 chars, pattern: `[a-zA-Z0-9_-]+`) |
| `--probes` | No | list | -- | List of probe definitions to create with the monitor |
| `--aggregation-period` | No | long | 60 | Metrics aggregation period: `30` or `60` seconds |
| `--client-token` | No | string | -- | Idempotent token |
| `--tags` | No | map | -- | Key-value tags (max 200) |

**Probe Structure (nested in `--probes`):**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `sourceArn` | **Yes** | string | ARN of the source subnet |
| `destination` | **Yes** | string | Destination IP address (IPv4 or IPv6) |
| `protocol` | **Yes** | string | `TCP` or `ICMP` |
| `destinationPort` | TCP only | integer | Port number (1-65536, required for TCP) |
| `packetSize` | No | integer | Packet size in bytes (56-8500) |
| `probeTags` | No | map | Tags for the probe |

**Output Schema:**
```json
{
    "monitorArn": "string",
    "monitorName": "string",
    "state": "PENDING|ACTIVE|INACTIVE|ERROR|DELETING",
    "aggregationPeriod": "long",
    "tags": { "string": "string" }
}
```

---

### 1.2 `get-monitor`

Returns details about a specific monitor including associated probes.

**Synopsis:**
```bash
aws networkmonitor get-monitor \
    --monitor-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name (1-200 chars) |

**Output Schema:**
```json
{
    "monitorArn": "string",
    "monitorName": "string",
    "state": "PENDING|ACTIVE|INACTIVE|ERROR|DELETING",
    "aggregationPeriod": "long",
    "tags": { "string": "string" },
    "probes": [
        {
            "probeId": "string",
            "probeArn": "string",
            "sourceArn": "string",
            "destination": "string",
            "destinationPort": "integer",
            "protocol": "TCP|ICMP",
            "packetSize": "integer",
            "addressFamily": "IPV4|IPV6",
            "vpcId": "string",
            "state": "PENDING|ACTIVE|INACTIVE|ERROR|DELETING|DELETED",
            "createdAt": "timestamp",
            "modifiedAt": "timestamp",
            "tags": { "string": "string" }
        }
    ],
    "createdAt": "timestamp",
    "modifiedAt": "timestamp"
}
```

---

### 1.3 `update-monitor`

Updates the aggregation period for an existing monitor.

**Synopsis:**
```bash
aws networkmonitor update-monitor \
    --monitor-name <value> \
    --aggregation-period <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name |
| `--aggregation-period` | **Yes** | long | -- | New aggregation period: `30` or `60` seconds |

**Output Schema:**
```json
{
    "monitorArn": "string",
    "monitorName": "string",
    "state": "PENDING|ACTIVE|INACTIVE|ERROR|DELETING",
    "aggregationPeriod": "long",
    "tags": { "string": "string" }
}
```

---

### 1.4 `delete-monitor`

Deletes a specified monitor. All probes associated with the monitor are automatically deleted.

**Synopsis:**
```bash
aws networkmonitor delete-monitor \
    --monitor-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name to delete |

**Output Schema:** None (HTTP 200 on success).

---

### 1.5 `list-monitors`

Returns a list of all monitors. **Paginated operation.**

**Synopsis:**
```bash
aws networkmonitor list-monitors \
    [--state <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--state` | No | string | -- | Filter by state |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "monitors": [
        {
            "monitorArn": "string",
            "monitorName": "string",
            "state": "PENDING|ACTIVE|INACTIVE|ERROR|DELETING",
            "aggregationPeriod": "long",
            "tags": { "string": "string" }
        }
    ],
    "nextToken": "string"
}
```
