# Credentials

### 2.1 `get-session-token`

Returns temporary security credentials for an IAM user. Typically used when MFA is required. The credentials cannot be used to call IAM or STS APIs except `assume-role` and `get-caller-identity`.

**Synopsis:**
```bash
aws sts get-session-token \
    [--duration-seconds <value>] \
    [--serial-number <value>] \
    [--token-code <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--duration-seconds` | No | integer | 43200 | Session duration in seconds. IAM user: 900-129600. Root: 900-3600 |
| `--serial-number` | No | string | None | ARN of the MFA device (hardware or virtual) |
| `--token-code` | No | string | None | MFA token code from device (6 digits). Required if `--serial-number` is provided |

**Output Schema:**
```json
{
    "Credentials": {
        "AccessKeyId": "string",
        "SecretAccessKey": "string",
        "SessionToken": "string",
        "Expiration": "timestamp"
    }
}
```

---

### 2.2 `get-federation-token`

Returns temporary security credentials for a federated user. Used by server-side applications to grant temporary access to AWS resources without creating IAM users. The calling IAM user's permissions are used to scope the federated user's permissions.

**Synopsis:**
```bash
aws sts get-federation-token \
    --name <value> \
    [--policy <value>] \
    [--policy-arns <value>] \
    [--duration-seconds <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the federated user (2-32 chars: letters, digits, `.+-_=@`) |
| `--policy` | No | string | None | Inline JSON session policy (max 2048 packed chars) |
| `--policy-arns` | No | list | None | ARNs of managed policies (max 10). Shorthand: `arn=string ...` |
| `--duration-seconds` | No | integer | 43200 | Session duration in seconds. IAM user: 900-129600. Root: 900-3600 |
| `--tags` | No | list | None | Session tags. Shorthand: `Key=string,Value=string ...` (max 50 tags) |

**Output Schema:**
```json
{
    "Credentials": {
        "AccessKeyId": "string",
        "SecretAccessKey": "string",
        "SessionToken": "string",
        "Expiration": "timestamp"
    },
    "FederatedUser": {
        "FederatedUserId": "string",
        "Arn": "string"
    },
    "PackedPolicySize": "integer"
}
```

---

### 2.3 `get-access-key-info`

Returns the account ID number of the AWS account that owns the specified access key. This can be used to determine which account an access key belongs to without needing permissions on the account.

**Synopsis:**
```bash
aws sts get-access-key-info \
    --access-key-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--access-key-id` | **Yes** | string | -- | The access key ID to look up |

**Output Schema:**
```json
{
    "Account": "string"
}
```
