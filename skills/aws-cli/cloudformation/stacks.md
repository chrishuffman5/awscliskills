# Stacks

### 1.1 `create-stack`

Creates a stack as specified in the template. After the call completes, CloudFormation uses the template to create all stack resources.

**Synopsis:**
```bash
aws cloudformation create-stack \
    --stack-name <value> \
    [--template-body <value>] \
    [--template-url <value>] \
    [--parameters <value>] \
    [--disable-rollback | --no-disable-rollback] \
    [--rollback-configuration <value>] \
    [--timeout-in-minutes <value>] \
    [--notification-arns <value>] \
    [--capabilities <value>] \
    [--resource-types <value>] \
    [--role-arn <value>] \
    [--on-failure <value>] \
    [--stack-policy-body <value>] \
    [--stack-policy-url <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--enable-termination-protection | --no-enable-termination-protection] \
    [--retain-except-on-create | --no-retain-except-on-create] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name (unique within a region). Must begin with a letter and contain only alphanumeric characters and hyphens |
| `--template-body` | No | string | -- | Template body (max 51,200 bytes). Use `file://` for local files |
| `--template-url` | No | string | -- | S3 URL of the template (max 460,800 bytes) |
| `--parameters` | No | list | None | Input parameters. Shorthand: `ParameterKey=string,ParameterValue=string,UsePreviousValue=boolean,ResolvedValue=string ...` |
| `--disable-rollback` | No | boolean | false | Disable rollback on stack creation failure |
| `--rollback-configuration` | No | structure | None | Rollback triggers. Structure: `RollbackTriggers=[{Arn=string,Type=string}],MonitoringTimeInMinutes=integer` |
| `--timeout-in-minutes` | No | integer | None | Time before stack creation times out |
| `--notification-arns` | No | list(string) | None | SNS topic ARNs for stack events |
| `--capabilities` | No | list(string) | None | `CAPABILITY_IAM`, `CAPABILITY_NAMED_IAM`, `CAPABILITY_AUTO_EXPAND` |
| `--resource-types` | No | list(string) | None | Resource types permitted to create |
| `--role-arn` | No | string | None | IAM role ARN for CloudFormation to assume |
| `--on-failure` | No | string | `ROLLBACK` | Action on failure: `DO_NOTHING`, `ROLLBACK`, `DELETE` |
| `--stack-policy-body` | No | string | None | Stack policy body (JSON) |
| `--stack-policy-url` | No | string | None | S3 URL of the stack policy |
| `--tags` | No | list | None | Tags (max 50). Shorthand: `Key=string,Value=string ...` |
| `--client-request-token` | No | string | None | Unique idempotency token |
| `--enable-termination-protection` | No | boolean | false | Enable termination protection |
| `--retain-except-on-create` | No | boolean | false | On failure, retain new resources except those created during this operation |

**Output Schema:**
```json
{
    "StackId": "string"
}
```

---

### 1.2 `update-stack`

Updates a stack as specified in the template.

**Synopsis:**
```bash
aws cloudformation update-stack \
    --stack-name <value> \
    [--template-body <value>] \
    [--template-url <value>] \
    [--use-previous-template | --no-use-previous-template] \
    [--stack-policy-during-update-body <value>] \
    [--stack-policy-during-update-url <value>] \
    [--parameters <value>] \
    [--capabilities <value>] \
    [--resource-types <value>] \
    [--role-arn <value>] \
    [--rollback-configuration <value>] \
    [--stack-policy-body <value>] \
    [--stack-policy-url <value>] \
    [--notification-arns <value>] \
    [--tags <value>] \
    [--disable-rollback | --no-disable-rollback] \
    [--client-request-token <value>] \
    [--retain-except-on-create | --no-retain-except-on-create] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--template-body` | No | string | -- | Updated template body |
| `--template-url` | No | string | -- | S3 URL of the updated template |
| `--use-previous-template` | No | boolean | false | Reuse the existing template |
| `--stack-policy-during-update-body` | No | string | None | Temporary stack policy during update |
| `--stack-policy-during-update-url` | No | string | None | S3 URL of temporary stack policy |
| `--parameters` | No | list | None | Updated parameters. Use `UsePreviousValue=true` to keep current values |
| `--capabilities` | No | list(string) | None | IAM capabilities acknowledgement |
| `--resource-types` | No | list(string) | None | Permitted resource types |
| `--role-arn` | No | string | None | IAM role ARN |
| `--rollback-configuration` | No | structure | None | Rollback triggers |
| `--stack-policy-body` | No | string | None | Updated stack policy |
| `--stack-policy-url` | No | string | None | S3 URL for updated stack policy |
| `--notification-arns` | No | list(string) | None | SNS topic ARNs |
| `--tags` | No | list | None | Updated tags |
| `--disable-rollback` | No | boolean | false | Disable rollback on failure |
| `--client-request-token` | No | string | None | Idempotency token |
| `--retain-except-on-create` | No | boolean | false | Retain new resources on failure |

**Output Schema:**
```json
{
    "StackId": "string"
}
```

---

### 1.3 `delete-stack`

Deletes a specified stack. All resources in the stack are deleted.

**Synopsis:**
```bash
aws cloudformation delete-stack \
    --stack-name <value> \
    [--retain-resources <value>] \
    [--role-arn <value>] \
    [--client-request-token <value>] \
    [--deletion-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--retain-resources` | No | list(string) | None | Logical IDs of resources to retain |
| `--role-arn` | No | string | None | IAM role ARN for deletion |
| `--client-request-token` | No | string | None | Idempotency token |
| `--deletion-mode` | No | string | `STANDARD` | `STANDARD` or `FORCE_DELETE_STACK` |

**Output:** No output on success.

---

### 1.4 `describe-stacks`

Returns the description for the specified stack. If no stack name is given, returns all stacks. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation describe-stacks \
    [--stack-name <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | No | string | None | Stack name or ID. Omit to list all stacks |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "Stacks": [
        {
            "StackId": "string",
            "StackName": "string",
            "ChangeSetId": "string",
            "Description": "string",
            "Parameters": [
                {
                    "ParameterKey": "string",
                    "ParameterValue": "string",
                    "UsePreviousValue": true|false,
                    "ResolvedValue": "string"
                }
            ],
            "CreationTime": "timestamp",
            "DeletionTime": "timestamp",
            "LastUpdatedTime": "timestamp",
            "RollbackConfiguration": {
                "RollbackTriggers": [
                    {
                        "Arn": "string",
                        "Type": "string"
                    }
                ],
                "MonitoringTimeInMinutes": "integer"
            },
            "StackStatus": "CREATE_IN_PROGRESS|CREATE_FAILED|CREATE_COMPLETE|...",
            "StackStatusReason": "string",
            "DisableRollback": true|false,
            "NotificationARNs": ["string"],
            "TimeoutInMinutes": "integer",
            "Capabilities": ["CAPABILITY_IAM|CAPABILITY_NAMED_IAM|CAPABILITY_AUTO_EXPAND"],
            "Outputs": [
                {
                    "OutputKey": "string",
                    "OutputValue": "string",
                    "Description": "string",
                    "ExportName": "string"
                }
            ],
            "RoleARN": "string",
            "Tags": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ],
            "EnableTerminationProtection": true|false,
            "ParentId": "string",
            "RootId": "string",
            "DriftInformation": {
                "StackDriftStatus": "DRIFTED|IN_SYNC|UNKNOWN|NOT_CHECKED",
                "LastCheckTimestamp": "timestamp"
            },
            "RetainExceptOnCreate": true|false,
            "DeletionMode": "STANDARD|FORCE_DELETE_STACK",
            "DetailedStatus": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `list-stacks`

Returns summary information for stacks. Deleted stacks are shown for 90 days. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-stacks \
    [--stack-status-filter <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-status-filter` | No | list(string) | None | Filter by status values (e.g., `CREATE_COMPLETE UPDATE_COMPLETE`) |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "StackSummaries": [
        {
            "StackId": "string",
            "StackName": "string",
            "TemplateDescription": "string",
            "CreationTime": "timestamp",
            "LastUpdatedTime": "timestamp",
            "DeletionTime": "timestamp",
            "StackStatus": "string",
            "StackStatusReason": "string",
            "ParentId": "string",
            "RootId": "string",
            "DriftInformation": {
                "StackDriftStatus": "string",
                "LastCheckTimestamp": "timestamp"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 1.6 `describe-stack-events`

Returns all stack-related events for a specified stack in reverse chronological order. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation describe-stack-events \
    --stack-name <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "StackEvents": [
        {
            "StackId": "string",
            "EventId": "string",
            "StackName": "string",
            "LogicalResourceId": "string",
            "PhysicalResourceId": "string",
            "ResourceType": "string",
            "Timestamp": "timestamp",
            "ResourceStatus": "string",
            "ResourceStatusReason": "string",
            "ResourceProperties": "string",
            "ClientRequestToken": "string",
            "HookType": "string",
            "HookStatus": "string",
            "HookStatusReason": "string",
            "HookInvocationPoint": "string",
            "HookFailureMode": "string",
            "DetailedStatus": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.7 `describe-stack-resources`

Returns all stack resources for a specified stack.

**Synopsis:**
```bash
aws cloudformation describe-stack-resources \
    --stack-name <value> \
    [--logical-resource-id <value>] \
    [--physical-resource-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--logical-resource-id` | No | string | None | Filter by logical resource ID |
| `--physical-resource-id` | No | string | None | Filter by physical resource ID |

**Output Schema:**
```json
{
    "StackResources": [
        {
            "StackName": "string",
            "StackId": "string",
            "LogicalResourceId": "string",
            "PhysicalResourceId": "string",
            "ResourceType": "string",
            "Timestamp": "timestamp",
            "ResourceStatus": "string",
            "ResourceStatusReason": "string",
            "Description": "string",
            "DriftInformation": {
                "StackResourceDriftStatus": "string",
                "LastCheckTimestamp": "timestamp"
            }
        }
    ]
}
```

---

### 1.8 `describe-stack-resource`

Returns a description of the specified resource in the specified stack.

**Synopsis:**
```bash
aws cloudformation describe-stack-resource \
    --stack-name <value> \
    --logical-resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--logical-resource-id` | **Yes** | string | -- | Logical resource ID |

**Output Schema:**
```json
{
    "StackResourceDetail": {
        "StackName": "string",
        "StackId": "string",
        "LogicalResourceId": "string",
        "PhysicalResourceId": "string",
        "ResourceType": "string",
        "LastUpdatedTimestamp": "timestamp",
        "ResourceStatus": "string",
        "ResourceStatusReason": "string",
        "Description": "string",
        "Metadata": "string",
        "DriftInformation": {
            "StackResourceDriftStatus": "string",
            "LastCheckTimestamp": "timestamp"
        }
    }
}
```

---

### 1.9 `list-stack-resources`

Returns summaries of all resources in a stack. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-stack-resources \
    --stack-name <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "StackResourceSummaries": [
        {
            "LogicalResourceId": "string",
            "PhysicalResourceId": "string",
            "ResourceType": "string",
            "LastUpdatedTimestamp": "timestamp",
            "ResourceStatus": "string",
            "ResourceStatusReason": "string",
            "DriftInformation": {
                "StackResourceDriftStatus": "string",
                "LastCheckTimestamp": "timestamp"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 1.10 `get-template`

Returns the template body for a specified stack or change set.

**Synopsis:**
```bash
aws cloudformation get-template \
    [--stack-name <value>] \
    [--change-set-name <value>] \
    [--template-stage <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | No | string | None | Stack name or ID |
| `--change-set-name` | No | string | None | Change set name or ID |
| `--template-stage` | No | string | None | `Original` or `Processed` |

**Output Schema:**
```json
{
    "TemplateBody": "string",
    "StagesAvailable": ["Original", "Processed"]
}
```

---

### 1.11 `get-template-summary`

Returns information about a template including parameters, capabilities, and resource types.

**Synopsis:**
```bash
aws cloudformation get-template-summary \
    [--template-body <value>] \
    [--template-url <value>] \
    [--stack-name <value>] \
    [--stack-set-name <value>] \
    [--call-as <value>] \
    [--template-summary-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-body` | No | string | None | Template body |
| `--template-url` | No | string | None | S3 URL of the template |
| `--stack-name` | No | string | None | Stack name or ID |
| `--stack-set-name` | No | string | None | Stack set name |
| `--call-as` | No | string | None | `SELF` or `DELEGATED_ADMIN` |
| `--template-summary-config` | No | structure | None | Configuration for template summary |

**Output Schema:**
```json
{
    "Parameters": [
        {
            "ParameterKey": "string",
            "DefaultValue": "string",
            "ParameterType": "string",
            "NoEcho": true|false,
            "Description": "string",
            "ParameterConstraints": {
                "AllowedValues": ["string"]
            }
        }
    ],
    "Description": "string",
    "Capabilities": ["string"],
    "CapabilitiesReason": "string",
    "ResourceTypes": ["string"],
    "Version": "string",
    "Metadata": "string",
    "DeclaredTransforms": ["string"],
    "ResourceIdentifierSummaries": [
        {
            "ResourceType": "string",
            "LogicalResourceIds": ["string"],
            "ResourceIdentifiers": ["string"]
        }
    ]
}
```

---

### 1.12 `validate-template`

Validates a specified template. CloudFormation checks template syntax.

**Synopsis:**
```bash
aws cloudformation validate-template \
    [--template-body <value>] \
    [--template-url <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-body` | No | string | None | Template body |
| `--template-url` | No | string | None | S3 URL of the template |

**Output Schema:**
```json
{
    "Parameters": [
        {
            "ParameterKey": "string",
            "DefaultValue": "string",
            "NoEcho": true|false,
            "Description": "string"
        }
    ],
    "Description": "string",
    "Capabilities": ["string"],
    "CapabilitiesReason": "string",
    "DeclaredTransforms": ["string"]
}
```

---

### 1.13 `get-stack-policy`

Returns the stack policy for a specified stack.

**Synopsis:**
```bash
aws cloudformation get-stack-policy \
    --stack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |

**Output Schema:**
```json
{
    "StackPolicyBody": "string"
}
```

---

### 1.14 `set-stack-policy`

Sets a stack policy for a specified stack.

**Synopsis:**
```bash
aws cloudformation set-stack-policy \
    --stack-name <value> \
    [--stack-policy-body <value>] \
    [--stack-policy-url <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--stack-policy-body` | No | string | None | Stack policy body (JSON) |
| `--stack-policy-url` | No | string | None | S3 URL of the stack policy |

**Output:** No output on success.

---

### 1.15 `cancel-update-stack`

Cancels an update on the specified stack. Only updates in `UPDATE_IN_PROGRESS` state can be cancelled.

**Synopsis:**
```bash
aws cloudformation cancel-update-stack \
    --stack-name <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--client-request-token` | No | string | None | Idempotency token |

**Output:** No output on success.

---

### 1.16 `continue-update-rollback`

Continues rolling back a stack that is in `UPDATE_ROLLBACK_FAILED` state. Use when some resources failed to return to their previous state.

**Synopsis:**
```bash
aws cloudformation continue-update-rollback \
    --stack-name <value> \
    [--role-arn <value>] \
    [--resources-to-skip <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--role-arn` | No | string | None | IAM role ARN |
| `--resources-to-skip` | No | list(string) | None | Logical IDs of resources to skip during rollback |
| `--client-request-token` | No | string | None | Idempotency token |

**Output:** No output on success (empty JSON `{}`).

---

### 1.17 `rollback-stack`

Rolls back the specified stack to the last known stable state.

**Synopsis:**
```bash
aws cloudformation rollback-stack \
    --stack-name <value> \
    [--role-arn <value>] \
    [--client-request-token <value>] \
    [--retain-except-on-create | --no-retain-except-on-create] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--role-arn` | No | string | None | IAM role ARN |
| `--client-request-token` | No | string | None | Idempotency token |
| `--retain-except-on-create` | No | boolean | false | Retain resources except those created during the failed operation |

**Output Schema:**
```json
{
    "StackId": "string"
}
```

---

### 1.18 `signal-resource`

Sends a signal to the specified resource with a success or failure status. Used with wait conditions and CreationPolicy.

**Synopsis:**
```bash
aws cloudformation signal-resource \
    --stack-name <value> \
    --logical-resource-id <value> \
    --unique-id <value> \
    --status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--logical-resource-id` | **Yes** | string | -- | Logical resource ID of the resource |
| `--unique-id` | **Yes** | string | -- | Unique ID for the signal (e.g., instance ID) |
| `--status` | **Yes** | string | -- | `SUCCESS` or `FAILURE` |

**Output:** No output on success.

---

### 1.19 `update-termination-protection`

Updates termination protection for the specified stack.

**Synopsis:**
```bash
aws cloudformation update-termination-protection \
    --stack-name <value> \
    --enable-termination-protection | --no-enable-termination-protection \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--enable-termination-protection` | **Yes** | boolean | -- | `--enable-termination-protection` to enable; `--no-enable-termination-protection` to disable |

**Output Schema:**
```json
{
    "StackId": "string"
}
```

---

### 1.20 `estimate-template-cost`

Returns an estimated monthly cost of a template based on the resources in it.

**Synopsis:**
```bash
aws cloudformation estimate-template-cost \
    [--template-body <value>] \
    [--template-url <value>] \
    [--parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-body` | No | string | None | Template body |
| `--template-url` | No | string | None | S3 URL of the template |
| `--parameters` | No | list | None | Input parameters. Shorthand: `ParameterKey=string,ParameterValue=string ...` |

**Output Schema:**
```json
{
    "Url": "string"
}
```

---

### 1.21 `deploy`

Deploys the specified CloudFormation template by creating or updating a stack. This is a higher-level command that wraps create-stack/update-stack with change set logic.

**Synopsis:**
```bash
aws cloudformation deploy \
    --template-file <value> \
    --stack-name <value> \
    [--s3-bucket <value>] \
    [--s3-prefix <value>] \
    [--kms-key-id <value>] \
    [--force-upload] \
    [--parameter-overrides <value> [<value>...]] \
    [--capabilities <value> [<value>...]] \
    [--no-execute-changeset] \
    [--role-arn <value>] \
    [--notification-arns <value> [<value>...]] \
    [--fail-on-empty-changeset | --no-fail-on-empty-changeset] \
    [--tags <value> [<value>...]] \
    [--disable-rollback | --no-disable-rollback]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-file` | **Yes** | string | -- | Path to local template file |
| `--stack-name` | **Yes** | string | -- | Stack name |
| `--s3-bucket` | No | string | None | S3 bucket to upload template to (required if template > 51,200 bytes) |
| `--s3-prefix` | No | string | None | Prefix for S3 template key |
| `--kms-key-id` | No | string | None | KMS key ID for encrypting artifacts in S3 |
| `--force-upload` | No | boolean | false | Force upload even if template hasn't changed |
| `--parameter-overrides` | No | list | None | Parameters as `Key=Value` pairs |
| `--capabilities` | No | list(string) | None | IAM capabilities: `CAPABILITY_IAM`, `CAPABILITY_NAMED_IAM`, `CAPABILITY_AUTO_EXPAND` |
| `--no-execute-changeset` | No | boolean | false | Create change set but don't execute it |
| `--role-arn` | No | string | None | IAM role ARN |
| `--notification-arns` | No | list(string) | None | SNS topic ARNs |
| `--fail-on-empty-changeset` | No | boolean | true | Fail if change set contains no changes. Use `--no-fail-on-empty-changeset` to return success |
| `--tags` | No | list | None | Tags as `Key=Value` pairs |
| `--disable-rollback` | No | boolean | false | Disable rollback on failure |

**Output:** Prints deployment status messages to stdout. No JSON output.

---

### 1.22 `package`

Packages local artifacts (Lambda code, nested templates, etc.) and uploads them to S3, then outputs a modified template referencing S3 locations.

**Synopsis:**
```bash
aws cloudformation package \
    --template-file <value> \
    --s3-bucket <value> \
    [--s3-prefix <value>] \
    [--kms-key-id <value>] \
    [--output-template-file <value>] \
    [--use-json] \
    [--force-upload] \
    [--metadata <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-file` | **Yes** | string | -- | Path to local template file |
| `--s3-bucket` | **Yes** | string | -- | S3 bucket for uploading artifacts |
| `--s3-prefix` | No | string | None | Prefix for S3 keys |
| `--kms-key-id` | No | string | None | KMS key ID for encrypting artifacts |
| `--output-template-file` | No | string | None | Output path for packaged template. Prints to stdout if not specified |
| `--use-json` | No | boolean | false | Output template in JSON (default is YAML) |
| `--force-upload` | No | boolean | false | Force upload even if artifacts haven't changed |
| `--metadata` | No | map | None | Metadata to attach to S3 objects |

**Output:** Modified template with S3 references (written to file or stdout).
