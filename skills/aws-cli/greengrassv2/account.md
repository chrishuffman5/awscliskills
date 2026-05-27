# Account & Service Role

### 4.1 `associate-service-role-to-account`

Associates an IAM service role with your account for Greengrass operations.

**Synopsis:**
```bash
aws greengrassv2 associate-service-role-to-account \
    --role-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-arn` | **Yes** | string | -- | ARN of the IAM service role |

**Output Schema:**
```json
{
    "associatedAt": "string"
}
```

---

### 4.2 `disassociate-service-role-from-account`

Removes the IAM service role from your account.

**Synopsis:**
```bash
aws greengrassv2 disassociate-service-role-from-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "disassociatedAt": "string"
}
```

---

### 4.3 `get-service-role-for-account`

Retrieves the IAM service role associated with your account.

**Synopsis:**
```bash
aws greengrassv2 get-service-role-for-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "associatedAt": "string",
    "roleArn": "string"
}
```
