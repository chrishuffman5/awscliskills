# Probes

### 2.1 `create-probe`

Create a probe within a monitor. New probes start in `PENDING` state and transition to `ACTIVE` within several minutes before CloudWatch metrics become available.

**Synopsis:**
```bash
aws networkmonitor create-probe \
    --monitor-name <value> \
    --probe <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name to associate the probe with (1-200 chars) |
| `--probe` | **Yes** | structure | -- | Probe definition (see below) |
| `--client-token` | No | string | -- | Idempotent token |
| `--tags` | No | map | -- | Key-value tags for the probe (max 200) |

**Probe Structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `sourceArn` | **Yes** | string | ARN of the source subnet |
| `destination` | **Yes** | string | Destination IP address (IPv4 or IPv6, 1-255 chars) |
| `protocol` | **Yes** | string | `TCP` or `ICMP` |
| `destinationPort` | TCP only | integer | Destination port (1-65536, required for TCP) |
| `packetSize` | No | integer | Packet size in bytes (56-8500) |
| `tags` | No | map | Tags for the probe |

**Shorthand syntax:**
```
sourceArn=string,destination=string,destinationPort=integer,protocol=string,packetSize=integer,tags={KeyName1=string,KeyName2=string}
```

**Output Schema:**
```json
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
```

---

### 2.2 `get-probe`

Returns the details about a probe.

**Synopsis:**
```bash
aws networkmonitor get-probe \
    --monitor-name <value> \
    --probe-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name |
| `--probe-id` | **Yes** | string | -- | Probe ID (pattern: `probe-[a-z0-9A-Z-]{21,64}`) |

**Output Schema:**
```json
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
```

---

### 2.3 `update-probe`

Updates a probe. You can update the destination, destination port, packet size, and state of a probe.

**Synopsis:**
```bash
aws networkmonitor update-probe \
    --monitor-name <value> \
    --probe-id <value> \
    [--state <value>] \
    [--destination <value>] \
    [--destination-port <value>] \
    [--protocol <value>] \
    [--packet-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name |
| `--probe-id` | **Yes** | string | -- | Probe ID to update |
| `--state` | No | string | -- | New probe state |
| `--destination` | No | string | -- | New destination IP address |
| `--destination-port` | No | integer | -- | New destination port (1-65536) |
| `--protocol` | No | string | -- | New protocol: `TCP` or `ICMP` |
| `--packet-size` | No | integer | -- | New packet size (56-8500) |

**Output Schema:**
```json
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
```

---

### 2.4 `delete-probe`

Deletes the specified probe from the monitor. Once deleted, the probe will no longer collect metrics.

**Synopsis:**
```bash
aws networkmonitor delete-probe \
    --monitor-name <value> \
    --probe-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name |
| `--probe-id` | **Yes** | string | -- | Probe ID to delete |

**Output Schema:** None (HTTP 200 on success).
