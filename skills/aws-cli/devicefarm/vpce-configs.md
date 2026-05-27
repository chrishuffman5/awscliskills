# VPCE Configurations

### 9.1 `create-vpce-configuration`

Creates a configuration record in Device Farm for your Amazon VPC endpoint.

**Synopsis:**
```bash
aws devicefarm create-vpce-configuration \
    --vpce-configuration-name <value> \
    --vpce-service-name <value> \
    --service-dns-name <value> \
    [--vpce-configuration-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpce-configuration-name` | **Yes** | string | -- | Friendly name for the VPC endpoint configuration |
| `--vpce-service-name` | **Yes** | string | -- | Name of the VPC endpoint service (e.g., `com.amazonaws.vpce.us-west-2.vpce-svc-id`) |
| `--service-dns-name` | **Yes** | string | -- | DNS name of the service running in your VPC |
| `--vpce-configuration-description` | No | string | None | Description of the VPC endpoint configuration |

**Output Schema:**
```json
{
    "vpceConfiguration": {
        "arn": "string",
        "vpceConfigurationName": "string",
        "vpceServiceName": "string",
        "serviceDnsName": "string",
        "vpceConfigurationDescription": "string"
    }
}
```

---

### 9.2 `delete-vpce-configuration`

Deletes a VPC endpoint configuration.

**Synopsis:**
```bash
aws devicefarm delete-vpce-configuration \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the VPC endpoint configuration to delete |

**Output Schema:**
```json
{}
```

---

### 9.3 `get-vpce-configuration`

Returns information about a VPC endpoint configuration.

**Synopsis:**
```bash
aws devicefarm get-vpce-configuration \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the VPC endpoint configuration |

**Output Schema:**
```json
{
    "vpceConfiguration": {
        "arn": "string",
        "vpceConfigurationName": "string",
        "vpceServiceName": "string",
        "serviceDnsName": "string",
        "vpceConfigurationDescription": "string"
    }
}
```

---

### 9.4 `list-vpce-configurations`

Returns information about all VPC endpoint configurations. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-vpce-configurations \
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
    "vpceConfigurations": [
        {
            "arn": "string",
            "vpceConfigurationName": "string",
            "vpceServiceName": "string",
            "serviceDnsName": "string",
            "vpceConfigurationDescription": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.5 `update-vpce-configuration`

Updates a VPC endpoint configuration.

**Synopsis:**
```bash
aws devicefarm update-vpce-configuration \
    --arn <value> \
    [--vpce-configuration-name <value>] \
    [--vpce-service-name <value>] \
    [--service-dns-name <value>] \
    [--vpce-configuration-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the VPC endpoint configuration to update |
| `--vpce-configuration-name` | No | string | None | Updated name |
| `--vpce-service-name` | No | string | None | Updated VPC endpoint service name |
| `--service-dns-name` | No | string | None | Updated DNS name |
| `--vpce-configuration-description` | No | string | None | Updated description |

**Output Schema:**
```json
{
    "vpceConfiguration": {
        "arn": "string",
        "vpceConfigurationName": "string",
        "vpceServiceName": "string",
        "serviceDnsName": "string",
        "vpceConfigurationDescription": "string"
    }
}
```
