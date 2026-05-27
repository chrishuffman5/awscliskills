# Scaling Groups

### 6.1 `create-kx-scaling-group`

Creates a new scaling group. A scaling group is a pool of shared compute resources that KX clusters can use.

**Synopsis:**
```bash
aws finspace create-kx-scaling-group \
    --environment-id <value> \
    --scaling-group-name <value> \
    --host-type <value> \
    --availability-zone-id <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--scaling-group-name` | **Yes** | string | -- | Scaling group name (3-63 chars) |
| `--host-type` | **Yes** | string | -- | Host type (e.g., `kx.sg.large`, `kx.sg.xlarge`, `kx.sg.16xlarge`) |
| `--availability-zone-id` | **Yes** | string | -- | Availability Zone ID |
| `--client-token` | No | string | Auto | Idempotency token |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "environmentId": "string",
    "scalingGroupName": "string",
    "hostType": "string",
    "availabilityZoneId": "string",
    "status": "CREATING|CREATE_FAILED|ACTIVE|DELETING|DELETED|DELETE_FAILED",
    "lastModifiedTimestamp": "timestamp",
    "createdTimestamp": "timestamp"
}
```

---

### 6.2 `delete-kx-scaling-group`

Deletes a scaling group. The scaling group must not have any clusters associated with it.

**Synopsis:**
```bash
aws finspace delete-kx-scaling-group \
    --environment-id <value> \
    --scaling-group-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--scaling-group-name` | **Yes** | string | -- | Scaling group name to delete |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None (HTTP 200 on success)

---

### 6.3 `get-kx-scaling-group`

Returns details of a specific scaling group.

**Synopsis:**
```bash
aws finspace get-kx-scaling-group \
    --environment-id <value> \
    --scaling-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--scaling-group-name` | **Yes** | string | -- | Scaling group name |

**Output Schema:**
```json
{
    "scalingGroupName": "string",
    "scalingGroupArn": "string",
    "hostType": "string",
    "clusters": ["string"],
    "availabilityZoneId": "string",
    "status": "CREATING|CREATE_FAILED|ACTIVE|DELETING|DELETED|DELETE_FAILED",
    "statusReason": "string",
    "lastModifiedTimestamp": "timestamp",
    "createdTimestamp": "timestamp"
}
```

---

### 6.4 `list-kx-scaling-groups`

Returns a list of all scaling groups in the specified environment. **Paginated operation.**

**Synopsis:**
```bash
aws finspace list-kx-scaling-groups \
    --environment-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--max-results` | No | integer | None | Maximum results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "scalingGroups": [
        {
            "scalingGroupName": "string",
            "hostType": "string",
            "clusters": ["string"],
            "availabilityZoneId": "string",
            "status": "string",
            "statusReason": "string",
            "lastModifiedTimestamp": "timestamp",
            "createdTimestamp": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
