# BYOIP (Bring Your Own IP)

Commands for managing BYOIP address ranges in AWS Global Accelerator.

### 6.1 `provision-byoip-cidr`

Provisions an IP address range for use with Global Accelerator. The address range must be /24 at most specific.

**Synopsis:**
```bash
aws globalaccelerator provision-byoip-cidr \
    --cidr <value> \
    --cidr-authorization-context <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cidr` | **Yes** | string | -- | IPv4 address range in CIDR notation (most specific: /24) |
| `--cidr-authorization-context` | **Yes** | structure | -- | Signed authorization. Shorthand: `Message=string,Signature=string` |

**Authorization Context Fields:**

| Field | Type | Description |
|-------|------|-------------|
| `Message` | string | Plain-text authorization message |
| `Signature` | string | Signed authorization message |

**Output Schema:**
```json
{
    "ByoipCidr": {
        "Cidr": "string",
        "State": "PENDING_PROVISIONING|READY|PENDING_ADVERTISING|ADVERTISING|PENDING_WITHDRAWING|PENDING_DEPROVISIONING|DEPROVISIONED|FAILED_PROVISION|FAILED_ADVERTISING|FAILED_WITHDRAW|FAILED_DEPROVISION",
        "Events": [
            {
                "Message": "string",
                "Timestamp": "timestamp"
            }
        ]
    }
}
```

---

### 6.2 `deprovision-byoip-cidr`

Releases a provisioned BYOIP address range. The range must not be advertised and must not be associated with any accelerator.

**Synopsis:**
```bash
aws globalaccelerator deprovision-byoip-cidr \
    --cidr <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cidr` | **Yes** | string | -- | CIDR block to deprovision |

**Output Schema:**
```json
{
    "ByoipCidr": {
        "Cidr": "string",
        "State": "string",
        "Events": []
    }
}
```

---

### 6.3 `advertise-byoip-cidr`

Starts advertising a provisioned BYOIP address range through the AWS global network. The range must be in `READY` state.

**Synopsis:**
```bash
aws globalaccelerator advertise-byoip-cidr \
    --cidr <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cidr` | **Yes** | string | -- | CIDR block to advertise |

**Output Schema:**
```json
{
    "ByoipCidr": {
        "Cidr": "string",
        "State": "string",
        "Events": []
    }
}
```

---

### 6.4 `withdraw-byoip-cidr`

Stops advertising a BYOIP address range. The range must be in `ADVERTISING` state and must not be associated with any accelerator.

**Synopsis:**
```bash
aws globalaccelerator withdraw-byoip-cidr \
    --cidr <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cidr` | **Yes** | string | -- | CIDR block to withdraw |

**Output Schema:**
```json
{
    "ByoipCidr": {
        "Cidr": "string",
        "State": "string",
        "Events": []
    }
}
```

---

### 6.5 `list-byoip-cidrs`

Lists all BYOIP address ranges. **Paginated operation.**

**Synopsis:**
```bash
aws globalaccelerator list-byoip-cidrs \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ByoipCidrs": [
        {
            "Cidr": "string",
            "State": "string",
            "Events": [
                {
                    "Message": "string",
                    "Timestamp": "timestamp"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```
