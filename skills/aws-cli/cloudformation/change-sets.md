# Change Sets

### 2.1 `create-change-set`

Creates a list of changes that will be applied to a stack so that you can review the changes before executing them. Can also be used to import resources.

**Synopsis:**
```bash
aws cloudformation create-change-set \
    --stack-name <value> \
    --change-set-name <value> \
    [--template-body <value>] \
    [--template-url <value>] \
    [--use-previous-template | --no-use-previous-template] \
    [--parameters <value>] \
    [--capabilities <value>] \
    [--resource-types <value>] \
    [--role-arn <value>] \
    [--rollback-configuration <value>] \
    [--notification-arns <value>] \
    [--tags <value>] \
    [--change-set-type <value>] \
    [--resources-to-import <value>] \
    [--include-nested-stacks | --no-include-nested-stacks] \
    [--on-stack-failure <value>] \
    [--import-existing-resources | --no-import-existing-resources] \
    [--description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Stack name or ID |
| `--change-set-name` | **Yes** | string | -- | Change set name (unique per stack, regex `[a-zA-Z][-a-zA-Z0-9]*`) |
| `--template-body` | No | string | None | Template body |
| `--template-url` | No | string | None | S3 URL of the template |
| `--use-previous-template` | No | boolean | false | Reuse the existing template |
| `--parameters` | No | list | None | Input parameters |
| `--capabilities` | No | list(string) | None | IAM capabilities acknowledgement |
| `--resource-types` | No | list(string) | None | Permitted resource types |
| `--role-arn` | No | string | None | IAM role ARN |
| `--rollback-configuration` | No | structure | None | Rollback triggers |
| `--notification-arns` | No | list(string) | None | SNS topic ARNs |
| `--tags` | No | list | None | Tags for the change set |
| `--change-set-type` | No | string | `UPDATE` | `CREATE`, `UPDATE`, or `IMPORT` |
| `--resources-to-import` | No | list | None | Resources to import. JSON: `[{"ResourceType":"AWS::S3::Bucket","LogicalResourceId":"MyBucket","ResourceIdentifier":{"BucketName":"my-bucket"}}]` |
| `--include-nested-stacks` | No | boolean | false | Include nested stacks in change set |
| `--on-stack-failure` | No | string | None | Action on failure: `DO_NOTHING`, `ROLLBACK`, `DELETE` |
| `--import-existing-resources` | No | boolean | false | Import existing resources |
| `--description` | No | string | None | Description of the change set |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "Id": "string",
    "StackId": "string"
}
```

---

### 2.2 `delete-change-set`

Deletes the specified change set. Deleting a change set does not modify the associated stack.

**Synopsis:**
```bash
aws cloudformation delete-change-set \
    --change-set-name <value> \
    [--stack-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--change-set-name` | **Yes** | string | -- | Change set name or ARN |
| `--stack-name` | No | string | None | Stack name (required if change-set-name is not an ARN) |

**Output:** No output on success (empty JSON `{}`).

---

### 2.3 `describe-change-set`

Returns the description for the specified change set.

**Synopsis:**
```bash
aws cloudformation describe-change-set \
    --change-set-name <value> \
    [--stack-name <value>] \
    [--include-property-values | --no-include-property-values] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--change-set-name` | **Yes** | string | -- | Change set name or ARN |
| `--stack-name` | No | string | None | Stack name |
| `--include-property-values` | No | boolean | false | Include property values in the response |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "ChangeSetName": "string",
    "ChangeSetId": "string",
    "StackId": "string",
    "StackName": "string",
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
    "ExecutionStatus": "UNAVAILABLE|AVAILABLE|EXECUTE_IN_PROGRESS|EXECUTE_COMPLETE|EXECUTE_FAILED|OBSOLETE",
    "Status": "CREATE_PENDING|CREATE_IN_PROGRESS|CREATE_COMPLETE|DELETE_FAILED|DELETE_COMPLETE|FAILED",
    "StatusReason": "string",
    "NotificationARNs": ["string"],
    "RollbackConfiguration": {},
    "Capabilities": ["string"],
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "Changes": [
        {
            "Type": "Resource",
            "HookInvocationCount": "integer",
            "ResourceChange": {
                "Action": "Add|Modify|Remove|Import|Dynamic",
                "LogicalResourceId": "string",
                "PhysicalResourceId": "string",
                "ResourceType": "string",
                "Replacement": "True|False|Conditional",
                "Scope": ["Properties", "Metadata", "CreationPolicy", "UpdatePolicy", "DeletionPolicy", "UpdateReplacePolicy", "Tags"],
                "Details": [
                    {
                        "Target": {
                            "Attribute": "string",
                            "Name": "string",
                            "RequiresRecreation": "Never|Conditionally|Always",
                            "Path": "string",
                            "BeforeValue": "string",
                            "AfterValue": "string",
                            "AttributeChangeType": "Add|Remove|Modify"
                        },
                        "Evaluation": "Static|Dynamic",
                        "ChangeSource": "ResourceReference|ParameterReference|ResourceAttribute|DirectModification|Automatic"
                    }
                ],
                "ChangeSetId": "string",
                "ModuleInfo": {
                    "TypeHierarchy": "string",
                    "LogicalIdHierarchy": "string"
                },
                "BeforeContext": "string",
                "AfterContext": "string"
            }
        }
    ],
    "IncludeNestedStacks": true|false,
    "ParentChangeSetId": "string",
    "RootChangeSetId": "string",
    "OnStackFailure": "string",
    "ImportExistingResources": true|false,
    "NextToken": "string"
}
```

---

### 2.4 `describe-change-set-hooks`

Returns hook-related information for a change set, including which hooks will be invoked and their status.

**Synopsis:**
```bash
aws cloudformation describe-change-set-hooks \
    --change-set-name <value> \
    [--stack-name <value>] \
    [--logical-resource-id <value>] \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--change-set-name` | **Yes** | string | -- | Change set name or ARN |
| `--stack-name` | No | string | None | Stack name |
| `--logical-resource-id` | No | string | None | Filter by logical resource ID |
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ChangeSetId": "string",
    "ChangeSetName": "string",
    "Hooks": [
        {
            "InvocationPoint": "PRE_PROVISION",
            "FailureMode": "FAIL|WARN",
            "TypeName": "string",
            "TypeVersionId": "string",
            "TypeConfigurationVersionId": "string",
            "TargetDetails": {
                "TargetType": "RESOURCE",
                "ResourceTargetDetails": {
                    "LogicalResourceId": "string",
                    "ResourceType": "string",
                    "ResourceAction": "Add|Modify|Remove|Import|Dynamic"
                }
            }
        }
    ],
    "Status": "PLANNING|PLANNED|UNAVAILABLE",
    "NextToken": "string",
    "StackId": "string",
    "StackName": "string"
}
```

---

### 2.5 `execute-change-set`

Updates a stack using the input from a change set. After the call completes, CloudFormation starts updating the stack.

**Synopsis:**
```bash
aws cloudformation execute-change-set \
    --change-set-name <value> \
    [--stack-name <value>] \
    [--client-request-token <value>] \
    [--disable-rollback | --no-disable-rollback] \
    [--retain-except-on-create | --no-retain-except-on-create] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--change-set-name` | **Yes** | string | -- | Change set name or ARN |
| `--stack-name` | No | string | None | Stack name |
| `--client-request-token` | No | string | None | Idempotency token |
| `--disable-rollback` | No | boolean | false | Disable rollback on failure |
| `--retain-except-on-create` | No | boolean | false | Retain resources on failure |

**Output:** No output on success (empty JSON `{}`).

---

### 2.6 `list-change-sets`

Returns a list of change sets for a stack. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-change-sets \
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
    "Summaries": [
        {
            "StackId": "string",
            "StackName": "string",
            "ChangeSetId": "string",
            "ChangeSetName": "string",
            "ExecutionStatus": "string",
            "Status": "string",
            "StatusReason": "string",
            "CreationTime": "timestamp",
            "Description": "string",
            "IncludeNestedStacks": true|false,
            "ParentChangeSetId": "string",
            "RootChangeSetId": "string",
            "ImportExistingResources": true|false
        }
    ],
    "NextToken": "string"
}
```
