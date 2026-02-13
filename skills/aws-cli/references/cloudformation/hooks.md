# Hooks

CloudFormation Hooks are extensions that proactively validate resource configurations before CloudFormation creates, updates, or deletes resources. Hooks use the type registry commands with hook-specific configuration.

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

---

### 11.1 Activating a Hook

Use `activate-type` to activate a published hook in your account.

**Synopsis:**
```bash
aws cloudformation activate-type \
    --type HOOK \
    --type-name <value> \
    --publisher-id <value> \
    [--type-name-alias <value>] \
    [--auto-update | --no-auto-update] \
    [--execution-role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Must be `HOOK` |
| `--type-name` | **Yes** | string | -- | Hook type name |
| `--publisher-id` | **Yes** | string | -- | Publisher ID of the hook |
| `--type-name-alias` | No | string | None | Alias for the hook |
| `--auto-update` | No | boolean | false | Auto-update on new versions |
| `--execution-role-arn` | No | string | None | Execution role ARN |

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

### 11.2 Configuring a Hook

Use `set-type-configuration` to configure a hook with its target stacks, failure mode, and properties.

**Synopsis:**
```bash
aws cloudformation set-type-configuration \
    --type HOOK \
    --type-name <value> \
    --configuration <value> \
    [--configuration-alias <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Must be `HOOK` |
| `--type-name` | **Yes** | string | -- | Hook type name |
| `--configuration` | **Yes** | string | -- | Hook configuration JSON |
| `--configuration-alias` | No | string | `default` | Configuration alias |

**Hook Configuration Structure:**
```json
{
    "CloudFormationConfiguration": {
        "HookConfiguration": {
            "TargetStacks": "ALL|NONE",
            "FailureMode": "FAIL|WARN",
            "Properties": {
                "hookPropertyKey": "hookPropertyValue"
            }
        }
    }
}
```

**Output Schema:**
```json
{
    "ConfigurationArn": "string"
}
```

---

### 11.3 Deactivating a Hook

Use `deactivate-type` to deactivate a hook in your account.

**Synopsis:**
```bash
aws cloudformation deactivate-type \
    --type HOOK \
    --type-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | Must be `HOOK` |
| `--type-name` | **Yes** | string | -- | Hook type name |

**Output:** No output on success (empty JSON `{}`).

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
