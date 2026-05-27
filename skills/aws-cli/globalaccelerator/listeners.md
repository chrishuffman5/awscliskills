# Listeners

### 2.1 `create-listener`

Creates a listener for a standard accelerator. A listener processes inbound connections based on port and protocol.

**Synopsis:**
```bash
aws globalaccelerator create-listener \
    --accelerator-arn <value> \
    --port-ranges <value> \
    --protocol <value> \
    [--client-affinity <value>] \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the accelerator |
| `--port-ranges` | **Yes** | list | -- | Port ranges (1-10). Shorthand: `FromPort=integer,ToPort=integer ...` |
| `--protocol` | **Yes** | string | -- | Protocol: `TCP` or `UDP` |
| `--client-affinity` | No | string | `NONE` | Client affinity: `NONE` or `SOURCE_IP` |
| `--idempotency-token` | No | string | None | Idempotency token (max 255 chars) |

**Output Schema:**
```json
{
    "Listener": {
        "ListenerArn": "string",
        "PortRanges": [
            {
                "FromPort": "integer",
                "ToPort": "integer"
            }
        ],
        "Protocol": "TCP|UDP",
        "ClientAffinity": "NONE|SOURCE_IP"
    }
}
```

---

### 2.2 `delete-listener`

Deletes a listener. All endpoint groups in the listener must be deleted first.

**Synopsis:**
```bash
aws globalaccelerator delete-listener \
    --listener-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener to delete |

**Output:** None on success.

---

### 2.3 `describe-listener`

Gets details about a listener.

**Synopsis:**
```bash
aws globalaccelerator describe-listener \
    --listener-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |

**Output Schema:** Same as `create-listener`.

---

### 2.4 `list-listeners`

Lists all listeners for an accelerator. **Paginated operation.**

**Synopsis:**
```bash
aws globalaccelerator list-listeners \
    --accelerator-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accelerator-arn` | **Yes** | string | -- | ARN of the accelerator |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Listeners": [
        {
            "ListenerArn": "string",
            "PortRanges": [
                {
                    "FromPort": "integer",
                    "ToPort": "integer"
                }
            ],
            "Protocol": "TCP|UDP",
            "ClientAffinity": "NONE|SOURCE_IP"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `update-listener`

Updates listener settings.

**Synopsis:**
```bash
aws globalaccelerator update-listener \
    --listener-arn <value> \
    [--port-ranges <value>] \
    [--protocol <value>] \
    [--client-affinity <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--listener-arn` | **Yes** | string | -- | ARN of the listener |
| `--port-ranges` | No | list | None | Updated port ranges |
| `--protocol` | No | string | None | `TCP` or `UDP` |
| `--client-affinity` | No | string | None | `NONE` or `SOURCE_IP` |

**Output Schema:** Same as `create-listener`.
