# Channel Placement Groups

### 10.1 `create-channel-placement-group`

Creates a channel placement group within a cluster to control channel placement on nodes.

**Synopsis:**
```bash
aws medialive create-channel-placement-group \
    --cluster-id <value> \
    [--name <value>] \
    [--nodes <value>] \
    [--request-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--name` | No | string | None | Placement group name |
| `--nodes` | No | list | None | Node IDs to include |
| `--request-id` | No | string | Auto | Idempotency token |
| `--tags` | No | map | None | Key-value tag pairs |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "ClusterId": "string",
    "Channels": ["string"],
    "Nodes": ["string"],
    "State": "UNASSIGNED|ASSIGNING|ASSIGNED|DELETING|DELETE_FAILED|DELETED"
}
```

---

### 10.2 `describe-channel-placement-group`

Describes a channel placement group.

**Synopsis:**
```bash
aws medialive describe-channel-placement-group \
    --cluster-id <value> \
    --channel-placement-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--channel-placement-group-id` | **Yes** | string | -- | Placement group ID |

**Output Schema:** Same as `create-channel-placement-group` output.

---

### 10.3 `update-channel-placement-group`

Updates a channel placement group.

**Synopsis:**
```bash
aws medialive update-channel-placement-group \
    --cluster-id <value> \
    --channel-placement-group-id <value> \
    [--name <value>] \
    [--nodes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--channel-placement-group-id` | **Yes** | string | -- | Placement group ID |
| `--name` | No | string | None | Updated name |
| `--nodes` | No | list | None | Updated node IDs |

**Output Schema:** Same as `create-channel-placement-group` output.

---

### 10.4 `delete-channel-placement-group`

Deletes a channel placement group.

**Synopsis:**
```bash
aws medialive delete-channel-placement-group \
    --cluster-id <value> \
    --channel-placement-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--channel-placement-group-id` | **Yes** | string | -- | Placement group ID to delete |

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

### 10.5 `list-channel-placement-groups`

Lists channel placement groups in a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-channel-placement-groups \
    --cluster-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "ChannelPlacementGroups": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "ClusterId": "string",
            "Channels": ["string"],
            "Nodes": ["string"],
            "State": "string"
        }
    ]
}
```
