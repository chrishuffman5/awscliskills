# Rotation

### 4.1 `rotate-secret`

Configures and/or immediately triggers rotation for a secret using a Lambda function.

**Synopsis:**
```bash
aws secretsmanager rotate-secret \
    --secret-id <value> \
    [--client-request-token <value>] \
    [--rotation-lambda-arn <value>] \
    [--rotation-rules <value>] \
    [--rotate-immediately | --no-rotate-immediately] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |
| `--client-request-token` | No | string | auto-generated | Idempotency token (32-64 chars) |
| `--rotation-lambda-arn` | No | string | None | ARN of the Lambda rotation function (max 2048 chars). Omit for managed rotation |
| `--rotation-rules` | No | structure | None | Rotation schedule configuration (see below) |
| `--rotate-immediately` | No | boolean | true | Whether to rotate immediately or wait for scheduled window |

**Rotation Rules Structure:**
```json
{
    "AutomaticallyAfterDays": long,
    "Duration": "string",
    "ScheduleExpression": "string"
}
```

| Field | Type | Description |
|-------|------|-------------|
| `AutomaticallyAfterDays` | long | Days between rotations (1-1000) |
| `Duration` | string | Rotation window duration, e.g. `"2h"` (2-3 chars, pattern `[0-9]+h`) |
| `ScheduleExpression` | string | Cron or rate expression, e.g. `"cron(0 8 1 * ? *)"` or `"rate(10 days)"` (1-256 chars) |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string",
    "VersionId": "string"
}
```

---

### 4.2 `cancel-rotate-secret`

Turns off automatic rotation and cancels any rotation currently in progress.

**Synopsis:**
```bash
aws secretsmanager cancel-rotate-secret \
    --secret-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |

**Output Schema:**
```json
{
    "ARN": "string",
    "Name": "string",
    "VersionId": "string"
}
```

---
