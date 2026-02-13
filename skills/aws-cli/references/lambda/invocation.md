# Invocation

### 2.1 `invoke`

Invokes a Lambda function synchronously or asynchronously.

**Synopsis:**
```bash
aws lambda invoke \
    --function-name <value> \
    [--invocation-type <value>] \
    [--log-type <value>] \
    [--client-context <value>] \
    [--payload <value>] \
    [--qualifier <value>] \
    [--cli-binary-format <value>] \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name, ARN, or partial ARN (1-256 chars) |
| `<outfile>` | **Yes** | string | -- | Filename to save response payload |
| `--invocation-type` | No | string | `RequestResponse` | Values: `RequestResponse` (sync), `Event` (async), `DryRun` (validate only) |
| `--log-type` | No | string | `None` | Set to `Tail` to include last 4KB of execution log (base64-encoded) |
| `--client-context` | No | string | -- | Base64-encoded client context data (max 3583 bytes) |
| `--payload` | No | blob | -- | JSON input (max 6 MB sync, 256 KB async). Use `'{"key":"value"}'` or `file://payload.json` |
| `--qualifier` | No | string | -- | Version or alias to invoke |
| `--cli-binary-format` | No | string | `base64` | Values: `base64`, `raw-in-base64-out`. Use `raw-in-base64-out` for literal JSON payloads |

**Output Schema:**
```json
{
    "StatusCode": "integer",
    "FunctionError": "string",
    "LogResult": "string",
    "Payload": "blob",
    "ExecutedVersion": "string"
}
```

| Field | Description |
|-------|-------------|
| `StatusCode` | `200` (sync success), `202` (async accepted), `204` (dry run) |
| `FunctionError` | Present if function returned an error (`Handled` or `Unhandled`) |
| `LogResult` | Last 4 KB of execution log, base64-encoded (only when `--log-type Tail`) |
| `Payload` | Written to `<outfile>`. Contains function response or error object |
| `ExecutedVersion` | Version that executed (e.g., `$LATEST`, `1`) |

---
