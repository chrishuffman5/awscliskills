# Policy Tools

### 5.1 `validate-policy`

Validates an IAM policy document against best practices. **Paginated operation.**

**Synopsis:**
```bash
aws accessanalyzer validate-policy \
    --policy-document <value> \
    --policy-type <value> \
    [--locale <value>] \
    [--validate-policy-resource-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-document` | **Yes** | string | -- | The JSON policy document to validate |
| `--policy-type` | **Yes** | string | -- | Policy type: `IDENTITY_POLICY`, `RESOURCE_POLICY`, `SERVICE_CONTROL_POLICY`, `RESOURCE_CONTROL_POLICY` |
| `--locale` | No | string | None | Locale for findings: `DE`, `EN`, `ES`, `FR`, `IT`, `JA`, `KO`, `PT_BR`, `ZH_CN`, `ZH_TW` |
| `--validate-policy-resource-type` | No | string | None | Resource type (only for `RESOURCE_POLICY`): `AWS::S3::Bucket`, `AWS::S3::AccessPoint`, `AWS::S3::MultiRegionAccessPoint`, `AWS::S3ObjectLambda::AccessPoint`, `AWS::IAM::AssumeRolePolicyDocument`, `AWS::DynamoDB::Table` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "findings": [
        {
            "findingDetails": "string",
            "findingType": "ERROR|SECURITY_WARNING|SUGGESTION|WARNING",
            "issueCode": "string",
            "learnMoreLink": "string",
            "locations": [
                {
                    "path": [
                        {
                            "index": "integer",
                            "key": "string",
                            "substring": {
                                "start": "integer",
                                "length": "integer"
                            },
                            "value": "string"
                        }
                    ],
                    "span": {
                        "start": {"line": "integer", "column": "integer", "offset": "integer"},
                        "end": {"line": "integer", "column": "integer", "offset": "integer"}
                    }
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

### 5.2 `check-access-not-granted`

Checks whether the specified access is not granted by a policy. Returns `PASS` if the policy does not grant the specified permissions, `FAIL` otherwise.

**Synopsis:**
```bash
aws accessanalyzer check-access-not-granted \
    --policy-document <value> \
    --access <value> \
    --policy-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-document` | **Yes** | string | -- | The JSON policy document |
| `--access` | **Yes** | list | -- | Access to check against (max 1 element with up to 100 actions and 100 resources) |
| `--policy-type` | **Yes** | string | -- | Policy type: `IDENTITY_POLICY`, `RESOURCE_POLICY` |

**Access Structure:**
```json
[
    {
        "actions": ["string"],
        "resources": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "result": "PASS|FAIL",
    "message": "string",
    "reasons": [
        {
            "description": "string",
            "statementIndex": "integer",
            "statementId": "string"
        }
    ]
}
```

---

### 5.3 `check-no-new-access`

Checks whether new access is allowed for an updated policy compared to a reference policy. Returns `PASS` if no new access is introduced, `FAIL` otherwise.

**Synopsis:**
```bash
aws accessanalyzer check-no-new-access \
    --new-policy-document <value> \
    --existing-policy-document <value> \
    --policy-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--new-policy-document` | **Yes** | string | -- | The JSON of the updated policy |
| `--existing-policy-document` | **Yes** | string | -- | The JSON of the reference policy |
| `--policy-type` | **Yes** | string | -- | Policy type: `IDENTITY_POLICY`, `RESOURCE_POLICY` |

**Output Schema:**
```json
{
    "result": "PASS|FAIL",
    "message": "string",
    "reasons": [
        {
            "description": "string",
            "statementIndex": "integer",
            "statementId": "string"
        }
    ]
}
```

---

### 5.4 `check-no-public-access`

Checks whether a resource policy grants public access.

**Synopsis:**
```bash
aws accessanalyzer check-no-public-access \
    --policy-document <value> \
    --resource-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-document` | **Yes** | string | -- | The JSON resource policy document |
| `--resource-type` | **Yes** | string | -- | The resource type (e.g., `AWS::S3::Bucket`, `AWS::KMS::Key`, `AWS::SQS::Queue`, etc.) |

**Output Schema:**
```json
{
    "result": "PASS|FAIL",
    "message": "string",
    "reasons": [
        {
            "description": "string",
            "statementIndex": "integer",
            "statementId": "string"
        }
    ]
}
```

---

### 5.5 `start-policy-generation`

Starts the policy generation process based on CloudTrail activity.

**Synopsis:**
```bash
aws accessanalyzer start-policy-generation \
    --policy-generation-details <value> \
    [--cloud-trail-details <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-generation-details` | **Yes** | structure | -- | Contains `principalArn` of the IAM entity (user or role) |
| `--cloud-trail-details` | No | structure | None | CloudTrail details for activity analysis |
| `--client-token` | No | string | None | Client token for idempotency |

**Policy Generation Details Structure:**
```json
{
    "principalArn": "string"
}
```

**CloudTrail Details Structure:**
```json
{
    "trails": [
        {
            "cloudTrailArn": "string",
            "regions": ["string"],
            "allRegions": true|false
        }
    ],
    "accessRole": "string",
    "startTime": "timestamp",
    "endTime": "timestamp"
}
```

**Output Schema:**
```json
{
    "jobId": "string"
}
```

---

### 5.6 `get-generated-policy`

Retrieves the policy generated using `start-policy-generation`. **Paginated operation.**

**Synopsis:**
```bash
aws accessanalyzer get-generated-policy \
    --job-id <value> \
    [--include-resource-placeholders | --no-include-resource-placeholders] \
    [--include-service-level-template | --no-include-service-level-template] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | The job ID from `start-policy-generation` |
| `--include-resource-placeholders` | No | boolean | false | Include resource placeholders in the policy |
| `--include-service-level-template` | No | boolean | false | Include service-level template |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "jobDetails": {
        "jobId": "string",
        "status": "IN_PROGRESS|SUCCEEDED|FAILED|CANCELED",
        "startedOn": "timestamp",
        "completedOn": "timestamp",
        "jobError": {
            "code": "string",
            "message": "string"
        }
    },
    "generatedPolicyResult": {
        "properties": {
            "isComplete": "boolean",
            "principalArn": "string",
            "cloudTrailProperties": {
                "trailProperties": [
                    {
                        "cloudTrailArn": "string",
                        "regions": ["string"],
                        "allRegions": "boolean"
                    }
                ],
                "startTime": "timestamp",
                "endTime": "timestamp"
            }
        },
        "generatedPolicies": [
            {
                "policy": "string"
            }
        ]
    }
}
```

---

### 5.7 `list-policy-generations`

Lists all policy generation requests. **Paginated operation.**

**Synopsis:**
```bash
aws accessanalyzer list-policy-generations \
    [--principal-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--principal-arn` | No | string | None | Filter by principal ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "policyGenerations": [
        {
            "jobId": "string",
            "principalArn": "string",
            "status": "IN_PROGRESS|SUCCEEDED|FAILED|CANCELED",
            "startedOn": "timestamp",
            "completedOn": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.8 `cancel-policy-generation`

Cancels an in-progress policy generation request.

**Synopsis:**
```bash
aws accessanalyzer cancel-policy-generation \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | The job ID of the policy generation request to cancel |

**Output:** None
