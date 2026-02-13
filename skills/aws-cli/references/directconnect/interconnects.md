# Interconnects

> **Note:** Interconnect commands are intended for Direct Connect partners only.

### 7.1 `create-interconnect`

Creates an interconnect between a Direct Connect partner's network and a specific Direct Connect location.

**Synopsis:**
```bash
aws directconnect create-interconnect \
    --interconnect-name <value> \
    --bandwidth <value> \
    --location <value> \
    [--lag-id <value>] \
    [--tags <value>] \
    [--provider-name <value>] \
    [--request-mac-sec | --no-request-mac-sec] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--interconnect-name` | **Yes** | string | -- | The name of the interconnect |
| `--bandwidth` | **Yes** | string | -- | The port bandwidth: `1Gbps`, `10Gbps`, `100Gbps` |
| `--location` | **Yes** | string | -- | The location of the interconnect |
| `--lag-id` | No | string | None | ID of the LAG to add the interconnect to |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |
| `--provider-name` | No | string | None | The service provider name |
| `--request-mac-sec` | No | boolean | false | Request MACsec support |

**Output Schema:**
```json
{
    "interconnectId": "string",
    "interconnectName": "string",
    "interconnectState": "requested|pending|available|down|deleting|deleted|unknown",
    "region": "string",
    "location": "string",
    "bandwidth": "string",
    "loaIssueTime": "timestamp",
    "lagId": "string",
    "awsDevice": "string",
    "jumboFrameCapable": "boolean",
    "awsDeviceV2": "string",
    "awsLogicalDeviceId": "string",
    "hasLogicalRedundancy": "unknown|yes|no",
    "tags": [{"key": "string", "value": "string"}],
    "providerName": "string",
    "macSecCapable": "boolean",
    "portEncryptionStatus": "string",
    "encryptionMode": "string",
    "macSecKeys": [
        {
            "secretARN": "string",
            "ckn": "string",
            "state": "associating|associated|disassociating|disassociated",
            "startOn": "string"
        }
    ]
}
```

---

### 7.2 `delete-interconnect`

Deletes the specified interconnect.

**Synopsis:**
```bash
aws directconnect delete-interconnect \
    --interconnect-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--interconnect-id` | **Yes** | string | -- | The ID of the interconnect |

**Output Schema:**
```json
{
    "interconnectState": "requested|pending|available|down|deleting|deleted|unknown"
}
```

---

### 7.3 `describe-interconnects`

Lists the interconnects owned by the account, or a specific interconnect. **Paginated.**

**Synopsis:**
```bash
aws directconnect describe-interconnects \
    [--interconnect-id <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--interconnect-id` | No | string | None | The ID of a specific interconnect |
| `--max-results` | No | integer | None | Maximum results (max 100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "interconnects": [
        {
            "interconnectId": "string",
            "interconnectName": "string",
            "interconnectState": "requested|pending|available|down|deleting|deleted|unknown",
            "region": "string",
            "location": "string",
            "bandwidth": "string",
            "loaIssueTime": "timestamp",
            "lagId": "string",
            "awsDevice": "string",
            "awsDeviceV2": "string",
            "awsLogicalDeviceId": "string",
            "jumboFrameCapable": "boolean",
            "hasLogicalRedundancy": "unknown|yes|no",
            "providerName": "string",
            "macSecCapable": "boolean",
            "portEncryptionStatus": "string",
            "encryptionMode": "string",
            "tags": [{"key": "string", "value": "string"}],
            "macSecKeys": []
        }
    ],
    "nextToken": "string"
}
```
