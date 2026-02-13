# Web Network Settings

> Commands use `aws workspaces-web` CLI prefix.

### 10.1 `create-network-settings`

Creates a network settings resource that defines VPC configuration for a web portal.

**Synopsis:**
```bash
aws workspaces-web create-network-settings \
    --vpc-id <value> \
    --subnet-ids <value> \
    --security-group-ids <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-id` | **Yes** | string | -- | The VPC ID |
| `--subnet-ids` | **Yes** | list(string) | -- | Subnet IDs (min 2, in different AZs) |
| `--security-group-ids` | **Yes** | list(string) | -- | Security group IDs (1-5) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "networkSettingsArn": "string"
}
```

---

### 10.2 `delete-network-settings`

Deletes network settings.

**Synopsis:**
```bash
aws workspaces-web delete-network-settings \
    --network-settings-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--network-settings-arn` | **Yes** | string | -- | The ARN of the network settings to delete |

**Output Schema:**
```json
{}
```

---

### 10.3 `get-network-settings`

Gets network settings.

**Synopsis:**
```bash
aws workspaces-web get-network-settings \
    --network-settings-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--network-settings-arn` | **Yes** | string | -- | The ARN of the network settings |

**Output Schema:**
```json
{
    "networkSettings": {
        "networkSettingsArn": "string",
        "associatedPortalArns": ["string"],
        "vpcId": "string",
        "subnetIds": ["string"],
        "securityGroupIds": ["string"]
    }
}
```

---

### 10.4 `list-network-settings`

Lists network settings. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces-web list-network-settings \
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
    "networkSettings": [
        {
            "networkSettingsArn": "string",
            "vpcId": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 10.5 `update-network-settings`

Updates network settings.

**Synopsis:**
```bash
aws workspaces-web update-network-settings \
    --network-settings-arn <value> \
    [--vpc-id <value>] \
    [--subnet-ids <value>] \
    [--security-group-ids <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--network-settings-arn` | **Yes** | string | -- | The ARN of the network settings to update |
| `--vpc-id` | No | string | None | New VPC ID |
| `--subnet-ids` | No | list(string) | None | New subnet IDs |
| `--security-group-ids` | No | list(string) | None | New security group IDs |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "networkSettings": {
        "networkSettingsArn": "string",
        "associatedPortalArns": ["string"],
        "vpcId": "string",
        "subnetIds": ["string"],
        "securityGroupIds": ["string"]
    }
}
```

---

### 10.6 `associate-network-settings`

Associates network settings with a web portal.

**Synopsis:**
```bash
aws workspaces-web associate-network-settings \
    --portal-arn <value> \
    --network-settings-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-arn` | **Yes** | string | -- | The ARN of the portal |
| `--network-settings-arn` | **Yes** | string | -- | The ARN of the network settings |

**Output Schema:**
```json
{
    "portalArn": "string",
    "networkSettingsArn": "string"
}
```

---

### 10.7 `disassociate-network-settings`

Disassociates network settings from a web portal.

**Synopsis:**
```bash
aws workspaces-web disassociate-network-settings \
    --portal-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-arn` | **Yes** | string | -- | The ARN of the portal to disassociate from |

**Output Schema:**
```json
{}
```
