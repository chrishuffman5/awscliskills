# Networks

### 9.1 `create-network`

Creates a network for MediaLive Anywhere on-premises deployments.

**Synopsis:**
```bash
aws medialive create-network \
    [--name <value>] \
    [--ip-pools <value>] \
    [--routes <value>] \
    [--request-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Network name (case-sensitive, unique) |
| `--ip-pools` | No | list | None | IP pool CIDR blocks to reserve |
| `--routes` | No | list | None | Routing configuration |
| `--request-id` | No | string | Auto | Idempotency token |
| `--tags` | No | map | None | Key-value tag pairs |

**IpPools:**
```json
[{"Cidr": "10.0.0.0/24"}]
```

**Routes:**
```json
[{"Cidr": "0.0.0.0/0", "Gateway": "10.0.0.1"}]
```

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "AssociatedClusterIds": ["string"],
    "IpPools": [{"Cidr": "string"}],
    "Routes": [{"Cidr": "string", "Gateway": "string"}],
    "State": "CREATING|CREATE_FAILED|ACTIVE|DELETING|DELETE_FAILED|DELETED"
}
```

---

### 9.2 `describe-network`

Describes a network.

**Synopsis:**
```bash
aws medialive describe-network \
    --network-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--network-id` | **Yes** | string | -- | Network ID |

**Output Schema:** Same as `create-network` output.

---

### 9.3 `update-network`

Updates a network's configuration.

**Synopsis:**
```bash
aws medialive update-network \
    --network-id <value> \
    [--name <value>] \
    [--ip-pools <value>] \
    [--routes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--network-id` | **Yes** | string | -- | Network ID to update |
| `--name` | No | string | None | Updated name |
| `--ip-pools` | No | list | None | Updated IP pools |
| `--routes` | No | list | None | Updated routes |

**Output Schema:** Same as `create-network` output.

---

### 9.4 `delete-network`

Deletes a network. Must not be associated with any clusters.

**Synopsis:**
```bash
aws medialive delete-network \
    --network-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--network-id` | **Yes** | string | -- | Network ID to delete |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "State": "DELETING"
}
```

---

### 9.5 `list-networks`

Lists networks. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-networks \
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
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Networks": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "AssociatedClusterIds": ["string"],
            "IpPools": [],
            "Routes": [],
            "State": "string"
        }
    ]
}
```
