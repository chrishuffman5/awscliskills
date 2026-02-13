# Outposts

### 1.1 `create-outpost`

Creates a new Outpost. An Outpost requires a site to host it.

**Synopsis:**
```bash
aws outposts create-outpost \
    --name <value> \
    --site-id <value> \
    --availability-zone <value> | --availability-zone-id <value> \
    [--description <value>] \
    [--supported-hardware-type <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the Outpost (1-255 chars) |
| `--site-id` | **Yes** | string | -- | ID of the site for this Outpost |
| `--availability-zone` | No | string | -- | Availability zone name (e.g., `us-east-1a`). Mutually exclusive with `--availability-zone-id` |
| `--availability-zone-id` | No | string | -- | Availability zone ID (e.g., `use1-az1`). Mutually exclusive with `--availability-zone` |
| `--description` | No | string | -- | Description of the Outpost |
| `--supported-hardware-type` | No | string | -- | Hardware type: `RACK` or `SERVER` |
| `--tags` | No | map | None | Tags as key-value pairs. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "Outpost": {
        "OutpostId": "string",
        "OwnerId": "string",
        "OutpostArn": "string",
        "SiteId": "string",
        "Name": "string",
        "Description": "string",
        "LifeCycleStatus": "string",
        "AvailabilityZone": "string",
        "AvailabilityZoneId": "string",
        "Tags": {
            "string": "string"
        },
        "SiteArn": "string",
        "SupportedHardwareType": "RACK|SERVER"
    }
}
```

---

### 1.2 `get-outpost`

Gets information about the specified Outpost.

**Synopsis:**
```bash
aws outposts get-outpost \
    --outpost-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-id` | **Yes** | string | -- | ID or ARN of the Outpost |

**Output Schema:**
```json
{
    "Outpost": {
        "OutpostId": "string",
        "OwnerId": "string",
        "OutpostArn": "string",
        "SiteId": "string",
        "Name": "string",
        "Description": "string",
        "LifeCycleStatus": "string",
        "AvailabilityZone": "string",
        "AvailabilityZoneId": "string",
        "Tags": {
            "string": "string"
        },
        "SiteArn": "string",
        "SupportedHardwareType": "RACK|SERVER"
    }
}
```

---

### 1.3 `list-outposts`

Lists the Outposts for your AWS account. **Paginated operation.**

**Synopsis:**
```bash
aws outposts list-outposts \
    [--lifecycle-status-filter <value>] \
    [--availability-zone-filter <value>] \
    [--availability-zone-id-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lifecycle-status-filter` | No | list(string) | None | Filter by lifecycle status: `ACTIVE`, `INSTALLING`, `PENDING`, etc. |
| `--availability-zone-filter` | No | list(string) | None | Filter by availability zone name |
| `--availability-zone-id-filter` | No | list(string) | None | Filter by availability zone ID |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Outposts": [
        {
            "OutpostId": "string",
            "OwnerId": "string",
            "OutpostArn": "string",
            "SiteId": "string",
            "Name": "string",
            "Description": "string",
            "LifeCycleStatus": "string",
            "AvailabilityZone": "string",
            "AvailabilityZoneId": "string",
            "Tags": {
                "string": "string"
            },
            "SiteArn": "string",
            "SupportedHardwareType": "RACK|SERVER"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-outpost`

Updates an Outpost name and description.

**Synopsis:**
```bash
aws outposts update-outpost \
    --outpost-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--supported-hardware-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-id` | **Yes** | string | -- | ID or ARN of the Outpost |
| `--name` | No | string | -- | Updated name |
| `--description` | No | string | -- | Updated description |
| `--supported-hardware-type` | No | string | -- | Hardware type: `RACK` or `SERVER` |

**Output Schema:**
```json
{
    "Outpost": {
        "OutpostId": "string",
        "OwnerId": "string",
        "OutpostArn": "string",
        "SiteId": "string",
        "Name": "string",
        "Description": "string",
        "LifeCycleStatus": "string",
        "AvailabilityZone": "string",
        "AvailabilityZoneId": "string",
        "Tags": {
            "string": "string"
        },
        "SiteArn": "string",
        "SupportedHardwareType": "RACK|SERVER"
    }
}
```

---

### 1.5 `delete-outpost`

Deletes the specified Outpost.

**Synopsis:**
```bash
aws outposts delete-outpost \
    --outpost-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-id` | **Yes** | string | -- | ID or ARN of the Outpost to delete |

**Output Schema:**
```json
{}
```

---

### 1.6 `get-outpost-instance-types`

Gets the instance types for the specified Outpost. **Paginated operation.**

**Synopsis:**
```bash
aws outposts get-outpost-instance-types \
    --outpost-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-id` | **Yes** | string | -- | ID or ARN of the Outpost |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "InstanceTypes": [
        {
            "InstanceType": "string"
        }
    ],
    "NextToken": "string",
    "OutpostId": "string",
    "OutpostArn": "string"
}
```

---

### 1.7 `get-outpost-supported-instance-types`

Gets the instance types that are supported by a specified Outpost for a given order. **Paginated operation.**

**Synopsis:**
```bash
aws outposts get-outpost-supported-instance-types \
    --outpost-identifier <value> \
    --order-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-identifier` | **Yes** | string | -- | ID or ARN of the Outpost |
| `--order-id` | **Yes** | string | -- | ID of the order |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "InstanceTypes": [
        {
            "InstanceType": "string"
        }
    ],
    "NextToken": "string"
}
```
