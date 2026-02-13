# Service Environments

### 7.1 `describe-service-environment`

Describes the Batch service environment.

**Synopsis:**
```bash
aws batch describe-service-environment \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No required parameters.

**Output Schema:**
```json
{
    "serviceEnvironment": {
        "serviceEnvironmentArn": "string",
        "serviceEnvironmentName": "string",
        "state": "string"
    }
}
```
