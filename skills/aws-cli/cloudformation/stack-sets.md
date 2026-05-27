# Stack Sets

### 3.1 `create-stack-set`

Creates a stack set. A stack set lets you create stacks in AWS accounts across regions by using a single template.

**Synopsis:**
```bash
aws cloudformation create-stack-set \
    --stack-set-name <value> \
    [--description <value>] \
    [--template-body <value>] \
    [--template-url <value>] \
    [--stack-id <value>] \
    [--parameters <value>] \
    [--capabilities <value>] \
    [--tags <value>] \
    [--administration-role-arn <value>] \
    [--execution-role-name <value>] \
    [--permission-model <value>] \
    [--auto-deployment <value>] \
    [--call-as <value>] \
    [--client-request-token <value>] \
    [--managed-execution <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name |
| `--description` | No | string | None | Description |
| `--template-body` | No | string | None | Template body |
| `--template-url` | No | string | None | S3 URL of the template |
| `--stack-id` | No | string | None | Stack ID to import as a stack set |
| `--parameters` | No | list | None | Input parameters |
| `--capabilities` | No | list(string) | None | IAM capabilities |
| `--tags` | No | list | None | Tags |
| `--administration-role-arn` | No | string | None | ARN of the administration role (SELF_MANAGED) |
| `--execution-role-name` | No | string | `AWSCloudFormationStackSetExecutionRole` | Execution role name in target accounts |
| `--permission-model` | No | string | `SELF_MANAGED` | `SELF_MANAGED` or `SERVICE_MANAGED` |
| `--auto-deployment` | No | structure | None | Auto deployment. Shorthand: `Enabled=boolean,RetainStacksOnAccountRemoval=boolean` |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |
| `--client-request-token` | No | string | None | Idempotency token |
| `--managed-execution` | No | structure | None | Managed execution. Shorthand: `Active=boolean` |

**Output Schema:**
```json
{
    "StackSetId": "string"
}
```

---

### 3.2 `update-stack-set`

Updates the stack set and all associated stack instances.

**Synopsis:**
```bash
aws cloudformation update-stack-set \
    --stack-set-name <value> \
    [--description <value>] \
    [--template-body <value>] \
    [--template-url <value>] \
    [--use-previous-template | --no-use-previous-template] \
    [--parameters <value>] \
    [--capabilities <value>] \
    [--tags <value>] \
    [--operation-preferences <value>] \
    [--administration-role-arn <value>] \
    [--execution-role-name <value>] \
    [--deployment-targets <value>] \
    [--permission-model <value>] \
    [--auto-deployment <value>] \
    [--operation-id <value>] \
    [--accounts <value>] \
    [--regions <value>] \
    [--call-as <value>] \
    [--managed-execution <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name or ID |
| `--description` | No | string | None | Updated description |
| `--template-body` | No | string | None | Updated template body |
| `--template-url` | No | string | None | S3 URL of updated template |
| `--use-previous-template` | No | boolean | false | Reuse current template |
| `--parameters` | No | list | None | Updated parameters |
| `--capabilities` | No | list(string) | None | IAM capabilities |
| `--tags` | No | list | None | Updated tags |
| `--operation-preferences` | No | structure | None | Operation preferences. Shorthand: `RegionConcurrencyType=SEQUENTIAL\|PARALLEL,RegionOrder=string,FailureToleranceCount=integer,FailureTolerancePercentage=integer,MaxConcurrentCount=integer,MaxConcurrentPercentage=integer,ConcurrencyMode=STRICT_FAILURE_TOLERANCE\|SOFT_FAILURE_TOLERANCE` |
| `--administration-role-arn` | No | string | None | Administration role ARN |
| `--execution-role-name` | No | string | None | Execution role name |
| `--deployment-targets` | No | structure | None | Deployment targets. Shorthand: `Accounts=string,AccountsUrl=string,OrganizationalUnitIds=string,AccountFilterType=NONE\|INTERSECTION\|DIFFERENCE\|UNION` |
| `--permission-model` | No | string | None | Permission model |
| `--auto-deployment` | No | structure | None | Auto deployment settings |
| `--operation-id` | No | string | None | Custom operation ID |
| `--accounts` | No | list(string) | None | Target account IDs |
| `--regions` | No | list(string) | None | Target regions |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |
| `--managed-execution` | No | structure | None | Managed execution settings |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 3.3 `delete-stack-set`

Deletes a stack set. All stack instances must be deleted first.

**Synopsis:**
```bash
aws cloudformation delete-stack-set \
    --stack-set-name <value> \
    [--call-as <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name or ID |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |

**Output:** No output on success (empty JSON `{}`).

---

### 3.4 `describe-stack-set`

Returns the description of the specified stack set.

**Synopsis:**
```bash
aws cloudformation describe-stack-set \
    --stack-set-name <value> \
    [--call-as <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name or ID |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |

**Output Schema:**
```json
{
    "StackSet": {
        "StackSetName": "string",
        "StackSetId": "string",
        "Description": "string",
        "Status": "ACTIVE|DELETED",
        "TemplateBody": "string",
        "Parameters": [
            {
                "ParameterKey": "string",
                "ParameterValue": "string",
                "UsePreviousValue": true|false,
                "ResolvedValue": "string"
            }
        ],
        "Capabilities": ["string"],
        "Tags": [
            {
                "Key": "string",
                "Value": "string"
            }
        ],
        "StackSetARN": "string",
        "AdministrationRoleARN": "string",
        "ExecutionRoleName": "string",
        "StackSetDriftDetectionDetails": {
            "DriftStatus": "DRIFTED|IN_SYNC|NOT_CHECKED",
            "DriftDetectionStatus": "COMPLETED|FAILED|PARTIAL_SUCCESS|IN_PROGRESS|STOPPED",
            "LastDriftCheckTimestamp": "timestamp",
            "TotalStackInstancesCount": "integer",
            "DriftedStackInstancesCount": "integer",
            "InSyncStackInstancesCount": "integer",
            "InProgressStackInstancesCount": "integer",
            "FailedStackInstancesCount": "integer"
        },
        "AutoDeployment": {
            "Enabled": true|false,
            "RetainStacksOnAccountRemoval": true|false
        },
        "PermissionModel": "SERVICE_MANAGED|SELF_MANAGED",
        "OrganizationalUnitIds": ["string"],
        "ManagedExecution": {
            "Active": true|false
        },
        "Regions": ["string"]
    }
}
```

---

### 3.5 `list-stack-sets`

Returns summary information about stack sets. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-stack-sets \
    [--status <value>] \
    [--call-as <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | None | `ACTIVE` or `DELETED` |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "Summaries": [
        {
            "StackSetName": "string",
            "StackSetId": "string",
            "Description": "string",
            "Status": "ACTIVE|DELETED",
            "AutoDeployment": {
                "Enabled": true|false,
                "RetainStacksOnAccountRemoval": true|false
            },
            "PermissionModel": "SERVICE_MANAGED|SELF_MANAGED",
            "DriftStatus": "DRIFTED|IN_SYNC|UNKNOWN|NOT_CHECKED",
            "LastDriftCheckTimestamp": "timestamp",
            "ManagedExecution": {
                "Active": true|false
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 3.6 `create-stack-instances`

Creates stack instances for the specified accounts in the specified regions.

**Synopsis:**
```bash
aws cloudformation create-stack-instances \
    --stack-set-name <value> \
    --regions <value> \
    [--accounts <value>] \
    [--deployment-targets <value>] \
    [--parameter-overrides <value>] \
    [--operation-preferences <value>] \
    [--operation-id <value>] \
    [--call-as <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name |
| `--regions` | **Yes** | list(string) | -- | Target regions |
| `--accounts` | No | list(string) | None | Target account IDs |
| `--deployment-targets` | No | structure | None | OU-based targeting |
| `--parameter-overrides` | No | list | None | Per-instance parameter overrides |
| `--operation-preferences` | No | structure | None | Operation preferences |
| `--operation-id` | No | string | None | Custom operation ID |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 3.7 `update-stack-instances`

Updates parameter overrides for stack instances in specified accounts and regions.

**Synopsis:**
```bash
aws cloudformation update-stack-instances \
    --stack-set-name <value> \
    --regions <value> \
    [--accounts <value>] \
    [--deployment-targets <value>] \
    [--parameter-overrides <value>] \
    [--operation-preferences <value>] \
    [--operation-id <value>] \
    [--call-as <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name |
| `--regions` | **Yes** | list(string) | -- | Target regions |
| `--accounts` | No | list(string) | None | Target account IDs |
| `--deployment-targets` | No | structure | None | OU-based targeting |
| `--parameter-overrides` | No | list | None | Parameter overrides |
| `--operation-preferences` | No | structure | None | Operation preferences |
| `--operation-id` | No | string | None | Custom operation ID |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 3.8 `delete-stack-instances`

Deletes stack instances for the specified accounts in specified regions.

**Synopsis:**
```bash
aws cloudformation delete-stack-instances \
    --stack-set-name <value> \
    --regions <value> \
    --retain-stacks | --no-retain-stacks \
    [--accounts <value>] \
    [--deployment-targets <value>] \
    [--operation-preferences <value>] \
    [--operation-id <value>] \
    [--call-as <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name |
| `--regions` | **Yes** | list(string) | -- | Target regions |
| `--retain-stacks` | **Yes** | boolean | -- | `--retain-stacks` keeps the stacks; `--no-retain-stacks` deletes them |
| `--accounts` | No | list(string) | None | Target account IDs |
| `--deployment-targets` | No | structure | None | OU-based targeting |
| `--operation-preferences` | No | structure | None | Operation preferences |
| `--operation-id` | No | string | None | Custom operation ID |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 3.9 `describe-stack-instance`

Returns the stack instance associated with the specified stack set, account, and region.

**Synopsis:**
```bash
aws cloudformation describe-stack-instance \
    --stack-set-name <value> \
    --stack-instance-account <value> \
    --stack-instance-region <value> \
    [--call-as <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name |
| `--stack-instance-account` | **Yes** | string | -- | Account ID |
| `--stack-instance-region` | **Yes** | string | -- | Region |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |

**Output Schema:**
```json
{
    "StackInstance": {
        "StackSetId": "string",
        "Region": "string",
        "Account": "string",
        "StackId": "string",
        "ParameterOverrides": [
            {
                "ParameterKey": "string",
                "ParameterValue": "string",
                "UsePreviousValue": true|false,
                "ResolvedValue": "string"
            }
        ],
        "Status": "CURRENT|OUTDATED|INOPERABLE",
        "StackInstanceStatus": {
            "DetailedStatus": "PENDING|RUNNING|SUCCEEDED|FAILED|CANCELLED|INOPERABLE|SKIPPED_SUSPENDED_ACCOUNT"
        },
        "StatusReason": "string",
        "OrganizationalUnitId": "string",
        "DriftStatus": "DRIFTED|IN_SYNC|UNKNOWN|NOT_CHECKED",
        "LastDriftCheckTimestamp": "timestamp",
        "LastOperationId": "string"
    }
}
```

---

### 3.10 `list-stack-instances`

Returns summary information about stack instances. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-stack-instances \
    --stack-set-name <value> \
    [--filters <value>] \
    [--stack-instance-account <value>] \
    [--stack-instance-region <value>] \
    [--call-as <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name |
| `--filters` | No | list | None | Filter by `DETAILED_STATUS`, `LAST_OPERATION_ID`, `DRIFT_STATUS` |
| `--stack-instance-account` | No | string | None | Filter by account |
| `--stack-instance-region` | No | string | None | Filter by region |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "Summaries": [
        {
            "StackSetId": "string",
            "Region": "string",
            "Account": "string",
            "StackId": "string",
            "Status": "CURRENT|OUTDATED|INOPERABLE",
            "StatusReason": "string",
            "StackInstanceStatus": {
                "DetailedStatus": "string"
            },
            "OrganizationalUnitId": "string",
            "DriftStatus": "DRIFTED|IN_SYNC|UNKNOWN|NOT_CHECKED",
            "LastDriftCheckTimestamp": "timestamp",
            "LastOperationId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.11 `describe-stack-set-operation`

Returns the description of a stack set operation.

**Synopsis:**
```bash
aws cloudformation describe-stack-set-operation \
    --stack-set-name <value> \
    --operation-id <value> \
    [--call-as <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name |
| `--operation-id` | **Yes** | string | -- | Operation ID |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |

**Output Schema:**
```json
{
    "StackSetOperation": {
        "OperationId": "string",
        "StackSetId": "string",
        "Action": "CREATE|UPDATE|DELETE|DETECT_DRIFT",
        "Status": "RUNNING|SUCCEEDED|FAILED|STOPPING|STOPPED|QUEUED",
        "OperationPreferences": {
            "RegionConcurrencyType": "SEQUENTIAL|PARALLEL",
            "RegionOrder": ["string"],
            "FailureToleranceCount": "integer",
            "FailureTolerancePercentage": "integer",
            "MaxConcurrentCount": "integer",
            "MaxConcurrentPercentage": "integer",
            "ConcurrencyMode": "string"
        },
        "RetainStacks": true|false,
        "AdministrationRoleARN": "string",
        "ExecutionRoleName": "string",
        "CreationTimestamp": "timestamp",
        "EndTimestamp": "timestamp",
        "DeploymentTargets": {
            "Accounts": ["string"],
            "AccountsUrl": "string",
            "OrganizationalUnitIds": ["string"],
            "AccountFilterType": "string"
        },
        "StackSetDriftDetectionDetails": {},
        "StatusReason": "string",
        "StatusDetails": {
            "FailedStackInstancesCount": "integer"
        }
    }
}
```

---

### 3.12 `list-stack-set-operations`

Returns summary information about operations performed on a stack set. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-stack-set-operations \
    --stack-set-name <value> \
    [--call-as <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "Summaries": [
        {
            "OperationId": "string",
            "Action": "CREATE|UPDATE|DELETE|DETECT_DRIFT",
            "Status": "RUNNING|SUCCEEDED|FAILED|STOPPING|STOPPED|QUEUED",
            "CreationTimestamp": "timestamp",
            "EndTimestamp": "timestamp",
            "StatusReason": "string",
            "StatusDetails": {
                "FailedStackInstancesCount": "integer"
            },
            "OperationPreferences": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 3.13 `list-stack-set-operation-results`

Returns summary information about the results of a stack set operation. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-stack-set-operation-results \
    --stack-set-name <value> \
    --operation-id <value> \
    [--call-as <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name |
| `--operation-id` | **Yes** | string | -- | Operation ID |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |
| `--filters` | No | list | None | Filter by `OPERATION_RESULT_STATUS` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "Summaries": [
        {
            "Account": "string",
            "Region": "string",
            "Status": "PENDING|RUNNING|SUCCEEDED|FAILED|CANCELLED",
            "StatusReason": "string",
            "AccountGateResult": {
                "Status": "SUCCEEDED|FAILED|SKIPPED",
                "StatusReason": "string"
            },
            "OrganizationalUnitId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.14 `stop-stack-set-operation`

Stops an in-progress operation on a stack set and its associated stack instances.

**Synopsis:**
```bash
aws cloudformation stop-stack-set-operation \
    --stack-set-name <value> \
    --operation-id <value> \
    [--call-as <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name |
| `--operation-id` | **Yes** | string | -- | Operation ID to stop |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |

**Output:** No output on success (empty JSON `{}`).

---

### 3.15 `import-stacks-to-stack-set`

Import existing stacks into a new or existing stack set.

**Synopsis:**
```bash
aws cloudformation import-stacks-to-stack-set \
    --stack-set-name <value> \
    [--stack-ids <value>] \
    [--stack-ids-url <value>] \
    [--organizational-unit-ids <value>] \
    [--operation-preferences <value>] \
    [--operation-id <value>] \
    [--call-as <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-set-name` | **Yes** | string | -- | Stack set name |
| `--stack-ids` | No | list(string) | None | Stack IDs to import |
| `--stack-ids-url` | No | string | None | S3 URL with list of stack IDs |
| `--organizational-unit-ids` | No | list(string) | None | OUs to scan for stacks to import |
| `--operation-preferences` | No | structure | None | Operation preferences |
| `--operation-id` | No | string | None | Custom operation ID |
| `--call-as` | No | string | `SELF` | `SELF` or `DELEGATED_ADMIN` |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```
