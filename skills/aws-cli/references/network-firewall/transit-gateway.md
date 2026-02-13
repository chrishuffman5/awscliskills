# Transit Gateway

### 7.1 `accept-network-firewall-transit-gateway-attachment`

Accepts a transit gateway attachment for a Network Firewall. The firewall must have been created with a transit gateway ID.

**Synopsis:**
```bash
aws network-firewall accept-network-firewall-transit-gateway-attachment \
    --transit-gateway-attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transit-gateway-attachment-id` | **Yes** | string | -- | Transit gateway attachment ID |

**Output Schema:**
```json
{
    "TransitGatewayAttachmentId": "string",
    "TransitGatewayAttachmentStatus": "CREATING|DELETING|DELETED|FAILED|ERROR|READY|PENDING_ACCEPTANCE|REJECTING|REJECTED"
}
```

---

### 7.2 `delete-network-firewall-transit-gateway-attachment`

Deletes a transit gateway attachment for a Network Firewall.

**Synopsis:**
```bash
aws network-firewall delete-network-firewall-transit-gateway-attachment \
    --transit-gateway-attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transit-gateway-attachment-id` | **Yes** | string | -- | Transit gateway attachment ID |

**Output Schema:**
```json
{
    "TransitGatewayAttachmentId": "string",
    "TransitGatewayAttachmentStatus": "DELETING"
}
```

---

### 7.3 `reject-network-firewall-transit-gateway-attachment`

Rejects a transit gateway attachment for a Network Firewall.

**Synopsis:**
```bash
aws network-firewall reject-network-firewall-transit-gateway-attachment \
    --transit-gateway-attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transit-gateway-attachment-id` | **Yes** | string | -- | Transit gateway attachment ID |

**Output Schema:**
```json
{
    "TransitGatewayAttachmentId": "string",
    "TransitGatewayAttachmentStatus": "REJECTING"
}
```
