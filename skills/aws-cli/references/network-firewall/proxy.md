# Proxy

### 8.1 `create-proxy`

Creates a forward proxy for the Network Firewall.

**Synopsis:**
```bash
aws network-firewall create-proxy \
    --proxy-name <value> \
    --firewall-arn <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--proxy-name` | **Yes** | string | -- | Proxy name (1-128 chars, alphanumeric and hyphens) |
| `--firewall-arn` | **Yes** | string | -- | ARN of the firewall |
| `--description` | No | string | None | Description (max 512 chars) |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "ProxyArn": "string",
    "Proxy": {
        "ProxyName": "string",
        "ProxyArn": "string",
        "FirewallArn": "string",
        "Description": "string",
        "Tags": []
    }
}
```

---

### 8.2 `delete-proxy`

Deletes the specified proxy.

**Synopsis:**
```bash
aws network-firewall delete-proxy \
    --proxy-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--proxy-arn` | **Yes** | string | -- | ARN of the proxy to delete |

**Output Schema:**
```json
{
    "ProxyArn": "string"
}
```

---

### 8.3 `describe-proxy`

Returns details about the specified proxy.

**Synopsis:**
```bash
aws network-firewall describe-proxy \
    --proxy-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--proxy-arn` | **Yes** | string | -- | ARN of the proxy |

**Output Schema:**
```json
{
    "Proxy": {
        "ProxyName": "string",
        "ProxyArn": "string",
        "FirewallArn": "string",
        "Description": "string",
        "Tags": []
    }
}
```

---

### 8.4 `list-proxies`

Lists all proxies. **Paginated operation.**

**Synopsis:**
```bash
aws network-firewall list-proxies \
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
    "Proxies": [
        {
            "ProxyName": "string",
            "ProxyArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `update-proxy`

Updates the specified proxy.

**Synopsis:**
```bash
aws network-firewall update-proxy \
    --proxy-arn <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--proxy-arn` | **Yes** | string | -- | ARN of the proxy |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "ProxyArn": "string",
    "Proxy": {
        "ProxyName": "string",
        "ProxyArn": "string",
        "FirewallArn": "string",
        "Description": "string"
    }
}
```

---

### 8.6 `create-proxy-configuration`

Creates a proxy configuration.

**Synopsis:**
```bash
aws network-firewall create-proxy-configuration \
    --proxy-arn <value> \
    --proxy-configuration-name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--proxy-arn` | **Yes** | string | -- | ARN of the proxy |
| `--proxy-configuration-name` | **Yes** | string | -- | Configuration name |
| `--description` | No | string | None | Description |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "ProxyConfigurationArn": "string",
    "ProxyConfiguration": {
        "ProxyConfigurationName": "string",
        "ProxyConfigurationArn": "string",
        "ProxyArn": "string",
        "Description": "string",
        "Tags": []
    }
}
```

---

### 8.7 `delete-proxy-configuration`

Deletes a proxy configuration.

**Synopsis:**
```bash
aws network-firewall delete-proxy-configuration \
    --proxy-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--proxy-configuration-arn` | **Yes** | string | -- | ARN of the proxy configuration |

**Output Schema:**
```json
{
    "ProxyConfigurationArn": "string"
}
```

---

### 8.8 `describe-proxy-configuration`

Returns details about a proxy configuration.

**Synopsis:**
```bash
aws network-firewall describe-proxy-configuration \
    --proxy-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--proxy-configuration-arn` | **Yes** | string | -- | ARN of the proxy configuration |

**Output Schema:**
```json
{
    "ProxyConfiguration": {
        "ProxyConfigurationName": "string",
        "ProxyConfigurationArn": "string",
        "ProxyArn": "string",
        "Description": "string",
        "Tags": []
    }
}
```

---

### 8.9 `list-proxy-configurations`

Lists proxy configurations. **Paginated operation.**

**Synopsis:**
```bash
aws network-firewall list-proxy-configurations \
    --proxy-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--proxy-arn` | **Yes** | string | -- | ARN of the proxy |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ProxyConfigurations": [
        {
            "ProxyConfigurationName": "string",
            "ProxyConfigurationArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.10 `update-proxy-configuration`

Updates a proxy configuration.

**Synopsis:**
```bash
aws network-firewall update-proxy-configuration \
    --proxy-configuration-arn <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--proxy-configuration-arn` | **Yes** | string | -- | ARN of the proxy configuration |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "ProxyConfigurationArn": "string",
    "ProxyConfiguration": {
        "ProxyConfigurationName": "string",
        "ProxyConfigurationArn": "string",
        "ProxyArn": "string",
        "Description": "string"
    }
}
```
