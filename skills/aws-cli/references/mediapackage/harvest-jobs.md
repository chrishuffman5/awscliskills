# Harvest Jobs

### 4.1 `create-harvest-job`

Creates a harvest job to extract a clip of live content from an origin endpoint and store it in S3.

**Synopsis:**
```bash
aws mediapackagev2 create-harvest-job \
    --channel-group-name <value> \
    --channel-name <value> \
    --origin-endpoint-name <value> \
    --harvested-manifests <value> \
    --schedule-configuration <value> \
    --destination <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--harvest-job-name <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group (1-256 chars) |
| `--channel-name` | **Yes** | string | -- | Name of the channel (1-256 chars) |
| `--origin-endpoint-name` | **Yes** | string | -- | Name of the origin endpoint (1-256 chars) |
| `--harvested-manifests` | **Yes** | structure | -- | Manifests to harvest (HLS, DASH, LL-HLS) |
| `--schedule-configuration` | **Yes** | structure | -- | Start and end time for the harvest window |
| `--destination` | **Yes** | structure | -- | S3 destination for harvested content |
| `--description` | No | string | None | Descriptive text (0-1024 chars) |
| `--client-token` | No | string | Auto | Idempotency token |
| `--harvest-job-name` | No | string | Auto | Unique name for the harvest job (1-256 chars) |
| `--tags` | No | map | None | Key-value tag pairs |

**HarvestedManifests:**
```json
{
    "HlsManifests": [{"ManifestName": "string"}],
    "DashManifests": [{"ManifestName": "string"}],
    "LowLatencyHlsManifests": [{"ManifestName": "string"}]
}
```

**ScheduleConfiguration:**
```json
{
    "StartTime": "2025-01-01T00:00:00Z",
    "EndTime": "2025-01-01T01:00:00Z"
}
```

**Destination:**
```json
{
    "S3Destination": {
        "BucketName": "my-harvest-bucket",
        "DestinationPath": "clips/"
    }
}
```

**Output Schema:**
```json
{
    "ChannelGroupName": "string",
    "ChannelName": "string",
    "OriginEndpointName": "string",
    "Destination": {
        "S3Destination": {
            "BucketName": "string",
            "DestinationPath": "string"
        }
    },
    "HarvestJobName": "string",
    "HarvestedManifests": {
        "HlsManifests": [{"ManifestName": "string"}],
        "DashManifests": [{"ManifestName": "string"}],
        "LowLatencyHlsManifests": [{"ManifestName": "string"}]
    },
    "Description": "string",
    "ScheduleConfiguration": {
        "StartTime": "timestamp",
        "EndTime": "timestamp"
    },
    "Arn": "string",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "Status": "QUEUED|IN_PROGRESS|CANCELLED|COMPLETED|FAILED",
    "ErrorMessage": "string",
    "ETag": "string",
    "Tags": {"string": "string"}
}
```

---

### 4.2 `get-harvest-job`

Retrieves details for a harvest job.

**Synopsis:**
```bash
aws mediapackagev2 get-harvest-job \
    --channel-group-name <value> \
    --channel-name <value> \
    --origin-endpoint-name <value> \
    --harvest-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--origin-endpoint-name` | **Yes** | string | -- | Name of the origin endpoint |
| `--harvest-job-name` | **Yes** | string | -- | Name of the harvest job |

**Output Schema:** Same as `create-harvest-job` output.

---

### 4.3 `list-harvest-jobs`

Lists harvest jobs for a channel. **Paginated operation.**

**Synopsis:**
```bash
aws mediapackagev2 list-harvest-jobs \
    --channel-group-name <value> \
    --channel-name <value> \
    --origin-endpoint-name <value> \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--origin-endpoint-name` | **Yes** | string | -- | Name of the origin endpoint |
| `--status` | No | string | None | Filter: `QUEUED`, `IN_PROGRESS`, `CANCELLED`, `COMPLETED`, `FAILED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Number of items per API call |
| `--max-items` | No | integer | None | Total number of items to return |

**Output Schema:**
```json
{
    "Items": [
        {
            "ChannelGroupName": "string",
            "ChannelName": "string",
            "OriginEndpointName": "string",
            "Destination": {
                "S3Destination": {"BucketName": "string", "DestinationPath": "string"}
            },
            "HarvestJobName": "string",
            "HarvestedManifests": {},
            "Description": "string",
            "ScheduleConfiguration": {
                "StartTime": "timestamp",
                "EndTime": "timestamp"
            },
            "Arn": "string",
            "CreatedAt": "timestamp",
            "ModifiedAt": "timestamp",
            "Status": "QUEUED|IN_PROGRESS|CANCELLED|COMPLETED|FAILED",
            "ErrorMessage": "string",
            "ETag": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `cancel-harvest-job`

Cancels a harvest job that is queued or in progress.

**Synopsis:**
```bash
aws mediapackagev2 cancel-harvest-job \
    --channel-group-name <value> \
    --channel-name <value> \
    --origin-endpoint-name <value> \
    --harvest-job-name <value> \
    [--e-tag <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--origin-endpoint-name` | **Yes** | string | -- | Name of the origin endpoint |
| `--harvest-job-name` | **Yes** | string | -- | Name of the harvest job to cancel |
| `--e-tag` | No | string | None | Expected ETag for concurrent update safety |

**Output:** None
