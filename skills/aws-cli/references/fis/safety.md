# Safety

### 5.1 `get-safety-lever`

Returns the current state of a safety lever. Safety levers are emergency controls that can stop all running experiments.

**Synopsis:**
```bash
aws fis get-safety-lever \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ARN of the safety lever |

**Output Schema:**
```json
{
    "safetyLever": {
        "id": "string",
        "arn": "string",
        "state": {
            "status": "disengaged|engaged",
            "reason": "string"
        }
    }
}
```

---

### 5.2 `update-safety-lever-state`

Updates the state of a safety lever. Engaging a safety lever stops all running experiments in the account and region.

**Synopsis:**
```bash
aws fis update-safety-lever-state \
    --id <value> \
    --state <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ARN of the safety lever |
| `--state` | **Yes** | structure | -- | New state. Shorthand: `status=disengaged\|engaged,reason=string` |

**Output Schema:**
```json
{
    "safetyLever": {
        "id": "string",
        "arn": "string",
        "state": {
            "status": "disengaged|engaged",
            "reason": "string"
        }
    }
}
```
