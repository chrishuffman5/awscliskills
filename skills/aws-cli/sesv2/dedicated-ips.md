# Dedicated IPs

### 7.1 `get-dedicated-ip`

Gets information about a specific dedicated IP address associated with your account.

**Synopsis:**
```bash
aws sesv2 get-dedicated-ip \
    --ip <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ip` | **Yes** | string | -- | The dedicated IP address to look up |

**Output Schema:**
```json
{
    "DedicatedIp": {
        "Ip": "string",
        "WarmupStatus": "IN_PROGRESS|DONE",
        "WarmupPercentage": "integer",
        "PoolName": "string"
    }
}
```

---

### 7.2 `get-dedicated-ips`

Lists all dedicated IP addresses associated with your account. **Paginated operation.**

**Synopsis:**
```bash
aws sesv2 get-dedicated-ips \
    [--pool-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-name` | No | string | None | Filter by dedicated IP pool name |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DedicatedIps": [
        {
            "Ip": "string",
            "WarmupStatus": "IN_PROGRESS|DONE",
            "WarmupPercentage": "integer",
            "PoolName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.3 `list-dedicated-ip-pools`

Lists all dedicated IP pools in the account. **Paginated operation.**

**Synopsis:**
```bash
aws sesv2 list-dedicated-ip-pools \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DedicatedIpPools": ["string"],
    "NextToken": "string"
}
```

---

### 7.4 `create-dedicated-ip-pool`

Creates a dedicated IP pool. Dedicated IPs can be assigned to pools to segment sending.

**Synopsis:**
```bash
aws sesv2 create-dedicated-ip-pool \
    --pool-name <value> \
    [--tags <value>] \
    [--scaling-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-name` | **Yes** | string | -- | Name for the dedicated IP pool |
| `--tags` | No | list | None | Tags to apply. Shorthand: `Key=string,Value=string ...` |
| `--scaling-mode` | No | string | `STANDARD` | Scaling mode: `STANDARD` or `MANAGED` |

**Output Schema:**
```json
{}
```

---

### 7.5 `delete-dedicated-ip-pool`

Deletes a dedicated IP pool. The pool must be empty (no dedicated IPs assigned).

**Synopsis:**
```bash
aws sesv2 delete-dedicated-ip-pool \
    --pool-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-name` | **Yes** | string | -- | Name of the pool to delete |

**Output Schema:**
```json
{}
```

---

### 7.6 `put-dedicated-ip-in-pool`

Moves a dedicated IP address to a different pool.

**Synopsis:**
```bash
aws sesv2 put-dedicated-ip-in-pool \
    --ip <value> \
    --destination-pool-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ip` | **Yes** | string | -- | Dedicated IP address to move |
| `--destination-pool-name` | **Yes** | string | -- | Target pool name |

**Output Schema:**
```json
{}
```

---

### 7.7 `put-dedicated-ip-warmup-attributes`

Sets the warmup percentage for a dedicated IP address.

**Synopsis:**
```bash
aws sesv2 put-dedicated-ip-warmup-attributes \
    --ip <value> \
    --warmup-percentage <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ip` | **Yes** | string | -- | Dedicated IP address |
| `--warmup-percentage` | **Yes** | integer | -- | Warmup percentage (1-100) |

**Output Schema:**
```json
{}
```
