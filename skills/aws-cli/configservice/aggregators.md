# Aggregators

### 6.1 `put-configuration-aggregator`

Creates or updates a configuration aggregator for multi-account/multi-region data aggregation.

**Synopsis:**
```bash
aws configservice put-configuration-aggregator \
    --configuration-aggregator-name <value> \
    [--account-aggregation-sources <value>] \
    [--organization-aggregation-source <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-aggregator-name` | **Yes** | string | -- | Name of the aggregator |
| `--account-aggregation-sources` | No | list | None | Source accounts for aggregation |
| `--organization-aggregation-source` | No | structure | None | Organization-wide aggregation source |
| `--tags` | No | list | None | Tags to apply |

**Account Aggregation Source Structure:**
```json
[
    {
        "AccountIds": ["string"],
        "AllAwsRegions": true|false,
        "AwsRegions": ["string"]
    }
]
```

**Organization Aggregation Source Structure:**
```json
{
    "RoleArn": "string",
    "AwsRegions": ["string"],
    "AllAwsRegions": true|false
}
```

**Output Schema:**
```json
{
    "ConfigurationAggregator": {
        "ConfigurationAggregatorName": "string",
        "ConfigurationAggregatorArn": "string",
        "AccountAggregationSources": [],
        "OrganizationAggregationSource": {
            "RoleArn": "string",
            "AwsRegions": ["string"],
            "AllAwsRegions": true|false
        },
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp",
        "CreatedBy": "string"
    }
}
```

---

### 6.2 `delete-configuration-aggregator`

Deletes the specified configuration aggregator and all aggregated data.

**Synopsis:**
```bash
aws configservice delete-configuration-aggregator \
    --configuration-aggregator-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-aggregator-name` | **Yes** | string | -- | Name of the aggregator to delete |

**Output Schema:**
```json
{}
```

---

### 6.3 `describe-configuration-aggregators`

Returns details about one or more configuration aggregators. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-configuration-aggregators \
    [--configuration-aggregator-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-aggregator-names` | No | list(string) | None | Specific aggregator names |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConfigurationAggregators": [
        {
            "ConfigurationAggregatorName": "string",
            "ConfigurationAggregatorArn": "string",
            "AccountAggregationSources": [],
            "OrganizationAggregationSource": {},
            "CreationTime": "timestamp",
            "LastUpdatedTime": "timestamp",
            "CreatedBy": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `describe-configuration-aggregator-sources-status`

Returns status information for sources within an aggregator. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-configuration-aggregator-sources-status \
    --configuration-aggregator-name <value> \
    [--update-status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-aggregator-name` | **Yes** | string | -- | Name of the aggregator |
| `--update-status` | No | list(string) | None | Filter by status: `FAILED`, `SUCCEEDED`, `OUTDATED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AggregatedSourceStatusList": [
        {
            "SourceId": "string",
            "SourceType": "ACCOUNT|ORGANIZATION",
            "AwsRegion": "string",
            "LastUpdateStatus": "FAILED|SUCCEEDED|OUTDATED",
            "LastUpdateTime": "timestamp",
            "LastErrorCode": "string",
            "LastErrorMessage": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `get-aggregate-compliance-details-by-config-rule`

Returns compliance details for a Config rule in an aggregator. **Paginated operation.**

**Synopsis:**
```bash
aws configservice get-aggregate-compliance-details-by-config-rule \
    --configuration-aggregator-name <value> \
    --config-rule-name <value> \
    --account-id <value> \
    --aws-region <value> \
    [--compliance-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-aggregator-name` | **Yes** | string | -- | Name of the aggregator |
| `--config-rule-name` | **Yes** | string | -- | Name of the Config rule |
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--aws-region` | **Yes** | string | -- | AWS region |
| `--compliance-type` | No | string | None | Filter: `COMPLIANT`, `NON_COMPLIANT`, `NOT_APPLICABLE`, `INSUFFICIENT_DATA` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AggregateEvaluationResults": [
        {
            "EvaluationResultIdentifier": {
                "EvaluationResultQualifier": {
                    "ConfigRuleName": "string",
                    "ResourceType": "string",
                    "ResourceId": "string"
                },
                "OrderingTimestamp": "timestamp"
            },
            "ComplianceType": "COMPLIANT|NON_COMPLIANT|NOT_APPLICABLE|INSUFFICIENT_DATA",
            "ResultRecordedTime": "timestamp",
            "ConfigRuleInvokedTime": "timestamp",
            "Annotation": "string",
            "AccountId": "string",
            "AwsRegion": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.6 `get-aggregate-config-rule-compliance-summary`

Returns aggregate compliance summary for Config rules across accounts and regions. **Paginated operation.**

**Synopsis:**
```bash
aws configservice get-aggregate-config-rule-compliance-summary \
    --configuration-aggregator-name <value> \
    [--filters <value>] \
    [--group-by-key <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-aggregator-name` | **Yes** | string | -- | Name of the aggregator |
| `--filters` | No | structure | None | Filter by account or region |
| `--group-by-key` | No | string | None | Group by: `ACCOUNT_ID`, `AWS_REGION` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GroupByKey": "string",
    "AggregateComplianceCounts": [
        {
            "GroupName": "string",
            "ComplianceSummary": {
                "CompliantResourceCount": {
                    "CappedCount": "integer",
                    "CapExceeded": true|false
                },
                "NonCompliantResourceCount": {
                    "CappedCount": "integer",
                    "CapExceeded": true|false
                },
                "ComplianceSummaryTimestamp": "timestamp"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 6.7 `get-aggregate-conformance-pack-compliance-summary`

Returns aggregate conformance pack compliance summary. **Paginated operation.**

**Synopsis:**
```bash
aws configservice get-aggregate-conformance-pack-compliance-summary \
    --configuration-aggregator-name <value> \
    [--filters <value>] \
    [--group-by-key <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-aggregator-name` | **Yes** | string | -- | Name of the aggregator |
| `--filters` | No | structure | None | Filter by account or region |
| `--group-by-key` | No | string | None | Group by: `ACCOUNT_ID`, `AWS_REGION` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AggregateConformancePackComplianceSummaries": [
        {
            "GroupName": "string",
            "ComplianceSummary": {
                "CompliantConformancePackCount": "integer",
                "NonCompliantConformancePackCount": "integer"
            }
        }
    ],
    "GroupByKey": "string",
    "NextToken": "string"
}
```

---

### 6.8 `get-aggregate-discovered-resource-counts`

Returns resource counts across accounts and regions in an aggregator. **Paginated operation.**

**Synopsis:**
```bash
aws configservice get-aggregate-discovered-resource-counts \
    --configuration-aggregator-name <value> \
    [--filters <value>] \
    [--group-by-key <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-aggregator-name` | **Yes** | string | -- | Name of the aggregator |
| `--filters` | No | structure | None | Filter by resource type, account, or region |
| `--group-by-key` | No | string | None | Group by: `RESOURCE_TYPE`, `ACCOUNT_ID`, `AWS_REGION` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TotalDiscoveredResources": "integer",
    "GroupByKey": "string",
    "GroupedResourceCounts": [
        {
            "GroupName": "string",
            "ResourceCount": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.9 `get-aggregate-resource-config`

Returns the configuration of a resource in an aggregated view.

**Synopsis:**
```bash
aws configservice get-aggregate-resource-config \
    --configuration-aggregator-name <value> \
    --resource-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-aggregator-name` | **Yes** | string | -- | Name of the aggregator |
| `--resource-identifier` | **Yes** | structure | -- | Resource identifier. Shorthand: `SourceAccountId=string,SourceRegion=string,ResourceId=string,ResourceType=string,ResourceName=string` |

**Output Schema:**
```json
{
    "ConfigurationItem": {
        "version": "string",
        "accountId": "string",
        "configurationItemCaptureTime": "timestamp",
        "configurationItemStatus": "OK|ResourceDiscovered|ResourceNotRecorded|ResourceDeleted|ResourceDeletedNotRecorded",
        "configurationStateId": "string",
        "configurationItemMD5Hash": "string",
        "arn": "string",
        "resourceType": "string",
        "resourceId": "string",
        "resourceName": "string",
        "awsRegion": "string",
        "availabilityZone": "string",
        "resourceCreationTime": "timestamp",
        "tags": {},
        "relatedEvents": ["string"],
        "relationships": [],
        "configuration": "string",
        "supplementaryConfiguration": {}
    }
}
```

---

### 6.10 `list-aggregate-discovered-resources`

Lists resources discovered by Config in an aggregator. **Paginated operation.**

**Synopsis:**
```bash
aws configservice list-aggregate-discovered-resources \
    --configuration-aggregator-name <value> \
    --resource-type <value> \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-aggregator-name` | **Yes** | string | -- | Name of the aggregator |
| `--resource-type` | **Yes** | string | -- | AWS resource type (e.g., `AWS::EC2::Instance`) |
| `--filters` | No | structure | None | Filter by account, region, or resource name/ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ResourceIdentifiers": [
        {
            "SourceAccountId": "string",
            "SourceRegion": "string",
            "ResourceId": "string",
            "ResourceType": "string",
            "ResourceName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.11 `batch-get-aggregate-resource-config`

Returns configuration items for multiple resources in an aggregator.

**Synopsis:**
```bash
aws configservice batch-get-aggregate-resource-config \
    --configuration-aggregator-name <value> \
    --resource-identifiers <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-aggregator-name` | **Yes** | string | -- | Name of the aggregator |
| `--resource-identifiers` | **Yes** | list | -- | List of resource identifiers (up to 100) |

**Output Schema:**
```json
{
    "BaseConfigurationItems": [
        {
            "version": "string",
            "accountId": "string",
            "configurationItemCaptureTime": "timestamp",
            "configurationItemStatus": "string",
            "arn": "string",
            "resourceType": "string",
            "resourceId": "string",
            "resourceName": "string",
            "awsRegion": "string",
            "configuration": "string",
            "supplementaryConfiguration": {}
        }
    ],
    "UnprocessedResourceIdentifiers": [
        {
            "SourceAccountId": "string",
            "SourceRegion": "string",
            "ResourceId": "string",
            "ResourceType": "string",
            "ResourceName": "string"
        }
    ]
}
```

---

### 6.12 `select-aggregate-resource-config`

Runs a SQL-like query against aggregate resource configuration data. **Paginated operation.**

**Synopsis:**
```bash
aws configservice select-aggregate-resource-config \
    --expression <value> \
    --configuration-aggregator-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--expression` | **Yes** | string | -- | SQL SELECT expression |
| `--configuration-aggregator-name` | **Yes** | string | -- | Name of the aggregator |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Results": ["string"],
    "QueryInfo": {
        "SelectFields": [
            {
                "Name": "string"
            }
        ]
    },
    "NextToken": "string"
}
```

---

### 6.13 `put-aggregation-authorization`

Authorizes the aggregator account and region to collect data from a source account and region.

**Synopsis:**
```bash
aws configservice put-aggregation-authorization \
    --authorized-account-id <value> \
    --authorized-aws-region <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authorized-account-id` | **Yes** | string | -- | 12-digit account ID of the aggregator account |
| `--authorized-aws-region` | **Yes** | string | -- | Region of the aggregator account |
| `--tags` | No | list | None | Tags to apply |

**Output Schema:**
```json
{
    "AggregationAuthorization": {
        "AggregationAuthorizationArn": "string",
        "AuthorizedAccountId": "string",
        "AuthorizedAwsRegion": "string",
        "CreationTime": "timestamp"
    }
}
```

---

### 6.14 `delete-aggregation-authorization`

Deletes the authorization for the specified aggregator account and region.

**Synopsis:**
```bash
aws configservice delete-aggregation-authorization \
    --authorized-account-id <value> \
    --authorized-aws-region <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authorized-account-id` | **Yes** | string | -- | 12-digit account ID |
| `--authorized-aws-region` | **Yes** | string | -- | Region of the aggregator account |

**Output Schema:**
```json
{}
```

---

### 6.15 `describe-aggregation-authorizations`

Returns a list of authorizations granted to various aggregator accounts and regions. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-aggregation-authorizations \
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
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AggregationAuthorizations": [
        {
            "AggregationAuthorizationArn": "string",
            "AuthorizedAccountId": "string",
            "AuthorizedAwsRegion": "string",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.16 `describe-pending-aggregation-requests`

Returns a list of all pending aggregation requests from source accounts. **Paginated operation.**

**Synopsis:**
```bash
aws configservice describe-pending-aggregation-requests \
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
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "PendingAggregationRequests": [
        {
            "RequesterAccountId": "string",
            "RequesterAwsRegion": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.17 `delete-pending-aggregation-request`

Deletes a pending aggregation request for an account and region.

**Synopsis:**
```bash
aws configservice delete-pending-aggregation-request \
    --requester-account-id <value> \
    --requester-aws-region <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--requester-account-id` | **Yes** | string | -- | 12-digit account ID of the requester |
| `--requester-aws-region` | **Yes** | string | -- | Region of the requester |

**Output Schema:**
```json
{}
```
