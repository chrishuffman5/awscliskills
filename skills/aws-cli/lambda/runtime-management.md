# Runtime Management

### 13.1 `get-runtime-management-config`

Returns the runtime management configuration for a function version.

**Synopsis:**
```bash
aws lambda get-runtime-management-config \
    --function-name <value> \
    [--qualifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--qualifier` | No | string | -- | Version or alias (1-128 chars) |

**Output Schema:**
```json
{
    "UpdateRuntimeOn": "Auto|Manual|FunctionUpdate",
    "RuntimeVersionArn": "string",
    "FunctionArn": "string"
}
```

---

### 13.2 `put-runtime-management-config`

Sets the runtime management configuration for a function version. Controls how Lambda updates the runtime.

**Synopsis:**
```bash
aws lambda put-runtime-management-config \
    --function-name <value> \
    --update-runtime-on <value> \
    [--qualifier <value>] \
    [--runtime-version-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--update-runtime-on` | **Yes** | string | -- | Values: `Auto` (auto-update), `Manual` (pin to specific version), `FunctionUpdate` (update only on function update) |
| `--qualifier` | No | string | -- | Version or alias (1-128 chars) |
| `--runtime-version-arn` | No | string | -- | Runtime version ARN (required when `Manual`) |

**Output Schema:**
```json
{
    "UpdateRuntimeOn": "Auto|Manual|FunctionUpdate",
    "FunctionArn": "string",
    "RuntimeVersionArn": "string"
}
```

---
