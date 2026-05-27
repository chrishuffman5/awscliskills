# Reports

### 1.1 `list-reports`

Lists all available compliance reports. **Paginated operation.**

**Synopsis:**
```bash
aws artifact list-reports \
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
    "reports": [
        {
            "id": "string",
            "name": "string",
            "state": "PUBLISHED|UNPUBLISHED",
            "arn": "string",
            "version": "long",
            "uploadState": "PROCESSING|COMPLETE|FAILED|FAULT",
            "description": "string",
            "periodStart": "timestamp",
            "periodEnd": "timestamp",
            "series": "string",
            "category": "string",
            "companyName": "string",
            "productName": "string",
            "statusMessage": "string",
            "acceptanceType": "PASSTHROUGH|EXPLICIT"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.2 `get-report-metadata`

Retrieves metadata for a specific compliance report.

**Synopsis:**
```bash
aws artifact get-report-metadata \
    --report-id <value> \
    [--report-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-id` | **Yes** | string | -- | Report ID (pattern: `report-[a-zA-Z0-9]{16}`) |
| `--report-version` | No | long | None | Report version number (min: 1) |

**Output Schema:**
```json
{
    "reportDetails": {
        "id": "string",
        "name": "string",
        "description": "string",
        "periodStart": "timestamp",
        "periodEnd": "timestamp",
        "createdAt": "timestamp",
        "lastModifiedAt": "timestamp",
        "deletedAt": "timestamp",
        "state": "PUBLISHED|UNPUBLISHED",
        "arn": "string",
        "series": "string",
        "category": "string",
        "companyName": "string",
        "productName": "string",
        "termArn": "string",
        "version": "long",
        "acceptanceType": "PASSTHROUGH|EXPLICIT",
        "sequenceNumber": "long",
        "uploadState": "PROCESSING|COMPLETE|FAILED|FAULT",
        "statusMessage": "string"
    }
}
```

---

### 1.3 `get-report`

Downloads a compliance report. You must first call `get-term-for-report` to obtain a `termToken`.

**Synopsis:**
```bash
aws artifact get-report \
    --report-id <value> \
    --term-token <value> \
    [--report-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-id` | **Yes** | string | -- | Report ID (pattern: `report-[a-zA-Z0-9]{16}`) |
| `--term-token` | **Yes** | string | -- | Download token from `get-term-for-report` (1-256 chars) |
| `--report-version` | No | long | None | Report version number (min: 1) |

**Output Schema:**
```json
{
    "documentPresignedUrl": "string"
}
```

> The `documentPresignedUrl` is a presigned S3 URL to access the report content (1-10240 chars).

---

### 1.4 `get-term-for-report`

Gets the terms associated with a report and returns a download token. This token is required to download the report with `get-report`.

**Synopsis:**
```bash
aws artifact get-term-for-report \
    --report-id <value> \
    [--report-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-id` | **Yes** | string | -- | Report ID (pattern: `report-[a-zA-Z0-9]{16}`) |
| `--report-version` | No | long | None | Report version number (min: 1) |

**Output Schema:**
```json
{
    "documentPresignedUrl": "string",
    "termToken": "string"
}
```

> The `documentPresignedUrl` is a presigned S3 URL to access the term content. The `termToken` is the unique token to use with `get-report`.

---

### 1.5 `list-report-versions`

Lists all versions of a specific report. **Paginated operation.**

**Synopsis:**
```bash
aws artifact list-report-versions \
    --report-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-id` | **Yes** | string | -- | Report ID (pattern: `report-[a-zA-Z0-9]{16}`) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "reports": [
        {
            "id": "string",
            "name": "string",
            "state": "PUBLISHED|UNPUBLISHED",
            "arn": "string",
            "version": "long",
            "uploadState": "PROCESSING|COMPLETE|FAILED|FAULT",
            "description": "string",
            "periodStart": "timestamp",
            "periodEnd": "timestamp",
            "series": "string",
            "category": "string",
            "companyName": "string",
            "productName": "string",
            "statusMessage": "string",
            "acceptanceType": "PASSTHROUGH|EXPLICIT"
        }
    ],
    "nextToken": "string"
}
```
