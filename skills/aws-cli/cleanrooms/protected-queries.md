# Protected Queries

## 6.1 `start-protected-query`

Starts a protected query within a membership.

**Synopsis:**
```bash
aws cleanrooms start-protected-query \
    --type <value> \
    --membership-identifier <value> \
    --sql-parameters <value> \
    --result-configuration <value> \
    [--compute-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Query type: `SQL` |
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--sql-parameters` | **Yes** | structure | -- | SQL query parameters |
| `--result-configuration` | **Yes** | structure | -- | Result output configuration |
| `--compute-configuration` | No | structure | None | Compute configuration for Spark queries |

**SQL Parameters Structure:**
```json
{
    "QueryString": "SELECT category, COUNT(*) as cnt FROM sales GROUP BY category",
    "AnalysisTemplateArn": "string",
    "Parameters": { "param1": "value1" }
}
```

**Result Configuration Structure:**
```json
{
    "OutputConfiguration": {
        "S3": {
            "ResultFormat": "CSV|PARQUET",
            "Bucket": "results-bucket",
            "KeyPrefix": "output/"
        },
        "Member": {
            "AccountId": "123456789012"
        }
    }
}
```

**Output Schema:**
```json
{
    "protectedQuery": {
        "id": "string",
        "membershipId": "string",
        "membershipArn": "string",
        "createTime": "timestamp",
        "sqlParameters": {},
        "status": "SUBMITTED|STARTED|COMPUTING|RESULT_READY|COMPLETED|FAILED|CANCELLED|TIMED_OUT",
        "resultConfiguration": {},
        "statistics": {
            "totalDurationInMillis": "long"
        },
        "result": {
            "output": {
                "s3": {
                    "location": "string"
                },
                "memberList": []
            }
        },
        "error": {
            "message": "string",
            "code": "string"
        }
    }
}
```

---

## 6.2 `get-protected-query`

Returns details for a protected query.

**Synopsis:**
```bash
aws cleanrooms get-protected-query \
    --membership-identifier <value> \
    --protected-query-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--protected-query-identifier` | **Yes** | string | -- | Protected query ID |

**Output Schema:**
```json
{
    "protectedQuery": {
        "id": "string",
        "membershipId": "string",
        "membershipArn": "string",
        "createTime": "timestamp",
        "sqlParameters": {},
        "status": "string",
        "resultConfiguration": {},
        "statistics": {},
        "result": {},
        "error": {}
    }
}
```

---

## 6.3 `list-protected-queries`

Lists protected queries for a membership. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-protected-queries \
    --membership-identifier <value> \
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
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--status` | No | string | None | Filter by status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "protectedQueries": [
        {
            "id": "string",
            "membershipId": "string",
            "membershipArn": "string",
            "createTime": "timestamp",
            "status": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 6.4 `update-protected-query`

Updates a protected query (used to cancel a query).

**Synopsis:**
```bash
aws cleanrooms update-protected-query \
    --membership-identifier <value> \
    --protected-query-identifier <value> \
    --target-status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--protected-query-identifier` | **Yes** | string | -- | Protected query ID |
| `--target-status` | **Yes** | string | -- | Target status: `CANCELLED` |

**Output Schema:**
```json
{
    "protectedQuery": {
        "id": "string",
        "status": "CANCELLED",
        "membershipId": "string"
    }
}
```

---

## 6.5 `start-protected-job`

Starts a protected job within a membership.

**Synopsis:**
```bash
aws cleanrooms start-protected-job \
    --job-type <value> \
    --membership-identifier <value> \
    [--job-parameters <value>] \
    [--result-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-type` | **Yes** | string | -- | Job type |
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--job-parameters` | No | structure | None | Job parameters |
| `--result-configuration` | No | structure | None | Result output configuration |

**Output Schema:**
```json
{
    "protectedJob": {
        "id": "string",
        "membershipId": "string",
        "status": "string",
        "createTime": "timestamp"
    }
}
```

---

## 6.6 `get-protected-job`

Returns details for a protected job.

**Synopsis:**
```bash
aws cleanrooms get-protected-job \
    --membership-identifier <value> \
    --protected-job-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--protected-job-identifier` | **Yes** | string | -- | Protected job ID |

**Output Schema:**
```json
{
    "protectedJob": {
        "id": "string",
        "membershipId": "string",
        "status": "string",
        "createTime": "timestamp",
        "result": {},
        "error": {}
    }
}
```

---

## 6.7 `list-protected-jobs`

Lists protected jobs for a membership. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-protected-jobs \
    --membership-identifier <value> \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--status` | No | string | None | Filter by status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "protectedJobs": [
        {
            "id": "string",
            "membershipId": "string",
            "status": "string",
            "createTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 6.8 `update-protected-job`

Updates a protected job.

**Synopsis:**
```bash
aws cleanrooms update-protected-job \
    --membership-identifier <value> \
    --protected-job-identifier <value> \
    --target-status <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--protected-job-identifier` | **Yes** | string | -- | Protected job ID |
| `--target-status` | **Yes** | string | -- | Target status: `CANCELLED` |

**Output Schema:**
```json
{
    "protectedJob": {
        "id": "string",
        "status": "string",
        "membershipId": "string"
    }
}
```
