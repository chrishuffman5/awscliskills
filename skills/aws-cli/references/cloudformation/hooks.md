# Hooks

CloudFormation Hooks are extensions that proactively validate resource configurations before CloudFormation creates, updates, or deletes resources.

## Overview

Hooks intercept CloudFormation operations and can either warn or prevent non-compliant resource configurations. They are registered and managed through the Type Registry but have hook-specific invocation points and failure modes.

### Hook Invocation Points
| Point | Description |
|-------|-------------|
| `PRE_PROVISION` | Invoked before CloudFormation provisions a resource |

### Hook Failure Modes
| Mode | Description |
|------|-------------|
| `FAIL` | Hook failure prevents the operation |
| `WARN` | Hook failure generates a warning but allows the operation |

### Hook Status Values
| Status | Description |
|--------|-------------|
| `HOOK_IN_PROGRESS` | Hook invocation is in progress |
| `HOOK_COMPLETE_SUCCEEDED` | Hook completed successfully |
| `HOOK_COMPLETE_FAILED` | Hook completed with failure |
| `HOOK_FAILED` | Hook invocation failed |

---

### 11.1 `list-hook-results`

Returns a list of hook invocation results for a given target (stack operation). **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-hook-results \
    --target-type <value> \
    --target-id <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-type` | **Yes** | string | -- | `CHANGE_SET`, `STACK`, `RESOURCE`, or `CLOUD_CONTROL` |
| `--target-id` | **Yes** | string | -- | Target ID (stack ID, change set ID, etc.) |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "TargetType": "CHANGE_SET|STACK|RESOURCE|CLOUD_CONTROL",
    "TargetId": "string",
    "HookResults": [
        {
            "InvocationPoint": "PRE_PROVISION",
            "FailureMode": "FAIL|WARN",
            "TypeName": "string",
            "TypeVersionId": "string",
            "TypeConfigurationVersionId": "string",
            "Status": "HOOK_IN_PROGRESS|HOOK_COMPLETE_SUCCEEDED|HOOK_COMPLETE_FAILED|HOOK_FAILED",
            "HookStatusReason": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 11.2 `get-hook-result`

Returns the details of a specific hook invocation result.

**Synopsis:**
```bash
aws cloudformation get-hook-result \
    --hook-result-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hook-result-id` | **Yes** | string | -- | Hook result ID |

**Output Schema:**
```json
{
    "InvocationPoint": "PRE_PROVISION",
    "FailureMode": "FAIL|WARN",
    "TypeName": "string",
    "TypeVersionId": "string",
    "TypeConfigurationVersionId": "string",
    "Status": "HOOK_IN_PROGRESS|HOOK_COMPLETE_SUCCEEDED|HOOK_COMPLETE_FAILED|HOOK_FAILED",
    "HookStatusReason": "string",
    "TargetType": "CHANGE_SET|STACK|RESOURCE|CLOUD_CONTROL",
    "TargetId": "string"
}
```

---

### Hook Events in Stack Events

When hooks are invoked during stack operations, they appear in `describe-stack-events` output with additional fields:

| Field | Description |
|-------|-------------|
| `HookType` | The type name of the hook |
| `HookStatus` | `HOOK_IN_PROGRESS`, `HOOK_COMPLETE_SUCCEEDED`, `HOOK_COMPLETE_FAILED` |
| `HookStatusReason` | Reason for the hook result |
| `HookInvocationPoint` | `PRE_PROVISION` |
| `HookFailureMode` | `FAIL` or `WARN` |
