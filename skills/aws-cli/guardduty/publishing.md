# Publishing

### 9.1 `create-publishing-destination`

Creates a publishing destination to export GuardDuty findings to. Currently supports S3 buckets.

**Synopsis:**
```bash
aws guardduty create-publishing-destination \
    --detector-id <value> \
    --destination-type <value> \
    --destination-properties <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--destination-type` | **Yes** | string | -- | Destination type: `S3` |
| `--destination-properties` | **Yes** | structure | -- | Properties of the publishing destination |
| `--client-token` | No | string | None | Idempotency token (0-64 chars) |

**Destination Properties Structure:**
```json
{
    "DestinationArn": "string",
    "KmsKeyArn": "string"
}
```

**Output Schema:**
```json
{
    "DestinationId": "string"
}
```

---

### 9.2 `delete-publishing-destination`

Deletes the publishing destination specified by the destination ID.

**Synopsis:**
```bash
aws guardduty delete-publishing-destination \
    --detector-id <value> \
    --destination-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--destination-id` | **Yes** | string | -- | The destination ID to delete |

**Output:** None (HTTP 200 on success)

---

### 9.3 `describe-publishing-destination`

Returns information about the publishing destination specified by the destination ID.

**Synopsis:**
```bash
aws guardduty describe-publishing-destination \
    --detector-id <value> \
    --destination-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--destination-id` | **Yes** | string | -- | The destination ID to describe |

**Output Schema:**
```json
{
    "DestinationId": "string",
    "DestinationType": "S3",
    "Status": "PENDING_VERIFICATION|PUBLISHING|UNABLE_TO_PUBLISH_FIX_DESTINATION_PROPERTY|STOPPED",
    "PublishingFailureStartTimestamp": "long",
    "DestinationProperties": {
        "DestinationArn": "string",
        "KmsKeyArn": "string"
    }
}
```

---

### 9.4 `list-publishing-destinations`

Returns a list of publishing destinations associated with the specified detector. **Paginated operation.**

**Synopsis:**
```bash
aws guardduty list-publishing-destinations \
    --detector-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Destinations": [
        {
            "DestinationId": "string",
            "DestinationType": "S3",
            "Status": "PENDING_VERIFICATION|PUBLISHING|UNABLE_TO_PUBLISH_FIX_DESTINATION_PROPERTY|STOPPED"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.5 `update-publishing-destination`

Updates the publishing destination specified by the destination ID.

**Synopsis:**
```bash
aws guardduty update-publishing-destination \
    --detector-id <value> \
    --destination-id <value> \
    [--destination-properties <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--detector-id` | **Yes** | string | -- | The detector ID (1-300 chars) |
| `--destination-id` | **Yes** | string | -- | The destination ID to update |
| `--destination-properties` | No | structure | None | Updated destination properties |

**Output:** None (HTTP 200 on success)
