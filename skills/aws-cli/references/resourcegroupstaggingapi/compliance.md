# Compliance

### 2.1 `get-compliance-summary`

Returns a summary of noncompliant resources grouped by specified dimensions. Compliance is evaluated against tag policies attached via AWS Organizations. **Paginated operation.**

**Synopsis:**
```bash
aws resourcegroupstaggingapi get-compliance-summary \
    [--target-id-filters <value>] \
    [--region-filters <value>] \
    [--resource-type-filters <value>] \
    [--tag-key-filters <value>] \
    [--group-by <value>] \
    [--max-results <value>] \
    [--pagination-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-id-filters` | No | list(string) | None | AWS account IDs or OU IDs to filter by |
| `--region-filters` | No | list(string) | None | AWS regions to filter by (e.g., `us-east-1`) |
| `--resource-type-filters` | No | list(string) | None | Resource types to filter by (e.g., `ec2:instance`) |
| `--tag-key-filters` | No | list(string) | None | Tag keys to evaluate compliance for |
| `--group-by` | No | list(string) | None | Grouping dimensions: `TARGET_ID`, `REGION`, `RESOURCE_TYPE` |
| `--max-results` | No | integer | None | Maximum number of results per page (1-1000) |
| `--pagination-token` | No | string | None | Token from previous response for pagination |

**Output Schema:**
```json
{
    "SummaryList": [
        {
            "LastUpdated": "string",
            "TargetId": "string",
            "TargetIdType": "ACCOUNT|OU|ROOT",
            "Region": "string",
            "ResourceType": "string",
            "NonCompliantResources": "integer"
        }
    ],
    "PaginationToken": "string"
}
```

---

### 2.2 `start-report-creation`

Generates a report that lists all tagged resources in accounts across your organization and whether each resource is compliant with the effective tag policy. The report is saved to an S3 bucket.

**Synopsis:**
```bash
aws resourcegroupstaggingapi start-report-creation \
    --s3-bucket <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-bucket` | **Yes** | string | -- | S3 bucket name where the report will be stored. Must be in the same region as the API call |

**Output Schema:**
```json
{}
```

> The command returns an empty object on success. Use `describe-report-creation` to check report status.

---

### 2.3 `describe-report-creation`

Describes the status of the `start-report-creation` operation. Returns the status, S3 location, and any error messages.

**Synopsis:**
```bash
aws resourcegroupstaggingapi describe-report-creation \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| _(none)_ | -- | -- | -- | This command takes no parameters beyond global options |

**Output Schema:**
```json
{
    "Status": "string",
    "S3Location": "string",
    "ErrorMessage": "string"
}
```

**Status Values:**

| Status | Description |
|--------|-------------|
| `RUNNING` | Report generation is in progress |
| `SUCCEEDED` | Report is complete and available at `S3Location` |
| `FAILED` | Report generation failed; see `ErrorMessage` |
