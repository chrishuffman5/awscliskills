# App UI

### 9.1 `get-cluster-session-credentials`

Returns temporary credentials to access application UIs (e.g., Spark UI, YARN ResourceManager) through the EMR console.

**Synopsis:**
```bash
aws emr get-cluster-session-credentials \
    --cluster-id <value> \
    --execution-role-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--execution-role-arn` | **Yes** | string | -- | IAM execution role ARN |

**Output Schema:**
```json
{
    "Credentials": {
        "UsernamePassword": {
            "Username": "string",
            "Password": "string"
        }
    },
    "ExpiresAt": "timestamp"
}
```
