# Permissions

### 9.1 `add-permission`

Adds a statement to a function's resource-based policy. Grants an AWS service or account permission to invoke the function.

**Synopsis:**
```bash
aws lambda add-permission \
    --function-name <value> \
    --statement-id <value> \
    --action <value> \
    --principal <value> \
    [--source-arn <value>] \
    [--source-account <value>] \
    [--event-source-token <value>] \
    [--qualifier <value>] \
    [--revision-id <value>] \
    [--principal-org-id <value>] \
    [--function-url-auth-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name, ARN, or partial ARN (1-256 chars) |
| `--statement-id` | **Yes** | string | -- | Unique statement identifier (1-100 chars) |
| `--action` | **Yes** | string | -- | Lambda action (e.g., `lambda:InvokeFunction`) |
| `--principal` | **Yes** | string | -- | AWS service (e.g., `s3.amazonaws.com`), account ID, or IAM ARN |
| `--source-arn` | No | string | -- | ARN of the invoking resource (restricts which resource can invoke) |
| `--source-account` | No | string | -- | Account ID that owns the invoking resource (12 digits) |
| `--event-source-token` | No | string | -- | Token for Alexa Smart Home (0-256 chars) |
| `--qualifier` | No | string | -- | Version or alias (1-128 chars) |
| `--revision-id` | No | string | -- | Only update if revision ID matches |
| `--principal-org-id` | No | string | -- | AWS Organizations ID (12-34 chars) |
| `--function-url-auth-type` | No | string | -- | Values: `NONE`, `AWS_IAM` |

**Output Schema:**
```json
{
    "Statement": "string (JSON policy statement)"
}
```

---

### 9.2 `remove-permission`

Removes a statement from a function's resource-based policy.

**Synopsis:**
```bash
aws lambda remove-permission \
    --function-name <value> \
    --statement-id <value> \
    [--qualifier <value>] \
    [--revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-256 chars) |
| `--statement-id` | **Yes** | string | -- | Statement identifier (1-100 chars) |
| `--qualifier` | No | string | -- | Version or alias (1-128 chars) |
| `--revision-id` | No | string | -- | Only update if revision ID matches |

**Output:** None on success.

---

### 9.3 `get-policy`

Returns the resource-based policy for a function, version, or alias.

**Synopsis:**
```bash
aws lambda get-policy \
    --function-name <value> \
    [--qualifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-256 chars) |
| `--qualifier` | No | string | -- | Version or alias (1-128 chars) |

**Output Schema:**
```json
{
    "Policy": "string (JSON policy document)",
    "RevisionId": "string"
}
```

---
