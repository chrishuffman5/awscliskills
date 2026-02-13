# MACsec

### 6.1 `associate-mac-sec-key`

Associates a MAC Security (MACsec) Connection Key Name (CKN)/Connectivity Association Key (CAK) pair with a connection or LAG.

**Synopsis:**
```bash
aws directconnect associate-mac-sec-key \
    --connection-id <value> \
    [--secret-arn <value>] \
    [--ckn <value>] \
    [--cak <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection, interconnect, or LAG |
| `--secret-arn` | No | string | None | The ARN of the MACsec secret key in Secrets Manager. Cannot be used with `--ckn`/`--cak` |
| `--ckn` | No | string | None | Connection Key Name (64 hex chars: 0-9, A-F). Must be used with `--cak` |
| `--cak` | No | string | None | Connectivity Association Key (64 hex chars: 0-9, A-F). Must be used with `--ckn` |

> **Note:** Either provide `--secret-arn` OR both `--ckn` and `--cak`. You cannot use both methods.

**Output Schema:**
```json
{
    "connectionId": "string",
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

### 6.2 `disassociate-mac-sec-key`

Removes the association between a MACsec secret key and a connection or LAG.

**Synopsis:**
```bash
aws directconnect disassociate-mac-sec-key \
    --connection-id <value> \
    --secret-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection, interconnect, or LAG |
| `--secret-arn` | **Yes** | string | -- | The ARN of the MACsec secret key |

**Output Schema:**
```json
{
    "connectionId": "string",
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
