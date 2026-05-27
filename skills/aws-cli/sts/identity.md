# Identity

### 3.1 `get-caller-identity`

Returns the IAM user or role whose credentials are used to call the operation. This is the most reliable way to determine the identity associated with the current credentials. No permissions are required to call this operation.

**Synopsis:**
```bash
aws sts get-caller-identity \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "UserId": "string",
    "Account": "string",
    "Arn": "string"
}
```

**Output Field Details:**

| Field | Description |
|-------|-------------|
| `UserId` | Unique identifier of the entity making the call. For IAM users: user ID. For assumed roles: `role-id:session-name`. For federated users: `account-id:caller-name` |
| `Account` | AWS account number (12 digits) |
| `Arn` | Full ARN of the caller (e.g., `arn:aws:iam::123456789012:user/Alice` or `arn:aws:sts::123456789012:assumed-role/RoleName/SessionName`) |

---

### 3.2 `decode-authorization-message`

Decodes an encoded authorization failure message returned by AWS when an API call is denied. The decoded message contains details about the authorization status, including which policies denied the request. The caller must have `sts:DecodeAuthorizationMessage` permission.

**Synopsis:**
```bash
aws sts decode-authorization-message \
    --encoded-message <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--encoded-message` | **Yes** | string | -- | The encoded authorization failure message |

**Output Schema:**
```json
{
    "DecodedMessage": "string"
}
```

**Decoded Message Contents:**
The `DecodedMessage` is a JSON string containing:
```json
{
    "allowed": false,
    "explicitDeny": true|false,
    "matchedStatements": {
        "items": [
            {
                "statementId": "string",
                "effect": "Allow|Deny",
                "principals": { "items": [{ "value": "string" }] },
                "principalGroups": { "items": [{ "value": "string" }] },
                "actions": { "items": [{ "value": "string" }] },
                "resources": { "items": [{ "value": "string" }] },
                "conditions": { "items": [{ "key": "string", "values": { "items": [{ "value": "string" }] } }] }
            }
        ]
    },
    "failures": { "items": [] },
    "context": {
        "principal": { "id": "string", "arn": "string", "account": "string" },
        "action": "string",
        "resource": "string",
        "conditions": { "items": [{ "key": "string", "values": { "items": [{ "value": "string" }] } }] }
    }
}
```
