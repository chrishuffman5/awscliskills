# Import Jobs

### 11.1 `start-import-job`

Starts a bulk import job for quick responses.

**Synopsis:**
```bash
aws qconnect start-import-job \
    --knowledge-base-id <value> \
    --import-job-type <value> \
    --upload-id <value> \
    [--client-token <value>] \
    [--metadata <value>] \
    [--external-source-configuration <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | KB ID or ARN (QUICK_RESPONSES type) |
| `--import-job-type` | **Yes** | string | -- | Must be `QUICK_RESPONSES` |
| `--upload-id` | **Yes** | string | -- | Upload ID from `start-content-upload` (1-1200 chars) |
| `--client-token` | No | string | None | Idempotency token |
| `--metadata` | No | map | None | Custom metadata (max 10 pairs) |
| `--external-source-configuration` | No | structure | None | External source (Amazon Connect) |

**External Source Configuration:**
```json
{
    "source": "AMAZON_CONNECT",
    "configuration": {
        "connectConfiguration": {
            "instanceId": "string"
        }
    }
}
```

**Output Schema:**
```json
{
    "importJob": {
        "importJobId": "string",
        "knowledgeBaseId": "string",
        "uploadId": "string",
        "knowledgeBaseArn": "string",
        "importJobType": "QUICK_RESPONSES",
        "status": "START_IN_PROGRESS|FAILED|COMPLETE|DELETE_IN_PROGRESS|DELETE_FAILED|DELETED",
        "url": "string",
        "failedRecordReport": "string",
        "urlExpiry": "timestamp",
        "createdTime": "timestamp",
        "lastModifiedTime": "timestamp",
        "metadata": {},
        "externalSourceConfiguration": {}
    }
}
```

---

### 11.2 `get-import-job`

Gets an import job.

**Synopsis:**
```bash
aws qconnect get-import-job \
    --knowledge-base-id <value> \
    --import-job-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--knowledge-base-id` | **Yes** | string | -- | KB ID or ARN |
| `--import-job-id` | **Yes** | string | -- | Import job ID |

**Output Schema:** Same as `start-import-job`.

---

### 11.3 `list-import-jobs`

Lists import jobs. **Paginated operation.**

**Synopsis:**
```bash
aws qconnect list-import-jobs \
    --knowledge-base-id <value> \
    [--next-token <value>] \
    [--max-results <value>]
```

**Output Schema:**
```json
{
    "importJobSummaries": [
        {
            "importJobId": "string",
            "knowledgeBaseId": "string",
            "knowledgeBaseArn": "string",
            "uploadId": "string",
            "importJobType": "string",
            "status": "string",
            "createdTime": "timestamp",
            "lastModifiedTime": "timestamp",
            "metadata": {},
            "externalSourceConfiguration": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 11.4 `delete-import-job`

Deletes an import job.

**Synopsis:**
```bash
aws qconnect delete-import-job \
    --knowledge-base-id <value> \
    --import-job-id <value>
```

**Output:** None
