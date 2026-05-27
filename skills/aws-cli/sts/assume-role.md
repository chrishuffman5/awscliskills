# Assume Role

### 1.1 `assume-role`

Returns temporary security credentials for assuming an IAM role. Use for cross-account access, privilege escalation within an account, or MFA-protected operations. The credentials consist of an access key ID, a secret access key, and a security token.

**Synopsis:**
```bash
aws sts assume-role \
    --role-arn <value> \
    --role-session-name <value> \
    [--policy-arns <value>] \
    [--policy <value>] \
    [--duration-seconds <value>] \
    [--tags <value>] \
    [--transitive-tag-keys <value>] \
    [--external-id <value>] \
    [--serial-number <value>] \
    [--token-code <value>] \
    [--source-identity <value>] \
    [--provided-contexts <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-arn` | **Yes** | string | -- | ARN of the role to assume |
| `--role-session-name` | **Yes** | string | -- | Identifier for the session (2-64 chars: letters, digits, `.+-_=@`) |
| `--policy-arns` | No | list | None | ARNs of managed policies to use as session policies (max 10). Shorthand: `arn=string ...` |
| `--policy` | No | string | None | Inline JSON session policy (max 2048 packed chars) |
| `--duration-seconds` | No | integer | 3600 | Session duration in seconds (900-43200, limited by role's MaxSessionDuration) |
| `--tags` | No | list | None | Session tags. Shorthand: `Key=string,Value=string ...` (max 50 tags) |
| `--transitive-tag-keys` | No | list(string) | None | Tag keys that persist in role chaining |
| `--external-id` | No | string | None | External ID for cross-account access (2-1224 chars) |
| `--serial-number` | No | string | None | ARN of MFA device or virtual MFA device ARN |
| `--token-code` | No | string | None | MFA token code from device (6 digits) |
| `--source-identity` | No | string | None | Source identity value that persists through role chaining |
| `--provided-contexts` | No | list | None | Context assertions. Shorthand: `ProviderArn=string,ContextAssertion=string ...` |

**Output Schema:**
```json
{
    "Credentials": {
        "AccessKeyId": "string",
        "SecretAccessKey": "string",
        "SessionToken": "string",
        "Expiration": "timestamp"
    },
    "AssumedRoleUser": {
        "AssumedRoleId": "string",
        "Arn": "string"
    },
    "PackedPolicySize": "integer",
    "SourceIdentity": "string"
}
```

---

### 1.2 `assume-role-with-saml`

Returns temporary security credentials for users authenticated via a SAML identity provider. Used for SSO/federated access through SAML 2.0.

**Synopsis:**
```bash
aws sts assume-role-with-saml \
    --role-arn <value> \
    --principal-arn <value> \
    --saml-assertion <value> \
    [--policy-arns <value>] \
    [--policy <value>] \
    [--duration-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-arn` | **Yes** | string | -- | ARN of the role to assume |
| `--principal-arn` | **Yes** | string | -- | ARN of the SAML provider in IAM |
| `--saml-assertion` | **Yes** | string | -- | Base64-encoded SAML authentication response (max 100000 chars) |
| `--policy-arns` | No | list | None | ARNs of managed policies for session policies (max 10). Shorthand: `arn=string ...` |
| `--policy` | No | string | None | Inline JSON session policy (max 2048 packed chars) |
| `--duration-seconds` | No | integer | 3600 | Session duration in seconds (900-43200, limited by role's MaxSessionDuration) |

**Output Schema:**
```json
{
    "Credentials": {
        "AccessKeyId": "string",
        "SecretAccessKey": "string",
        "SessionToken": "string",
        "Expiration": "timestamp"
    },
    "AssumedRoleUser": {
        "AssumedRoleId": "string",
        "Arn": "string"
    },
    "PackedPolicySize": "integer",
    "Subject": "string",
    "SubjectType": "string",
    "Issuer": "string",
    "Audience": "string",
    "NameQualifier": "string",
    "SourceIdentity": "string"
}
```

---

### 1.3 `assume-role-with-web-identity`

Returns temporary security credentials for users authenticated via an OIDC-compatible identity provider (e.g., Amazon Cognito, Google, Facebook, or any OIDC provider). Commonly used for mobile and web applications, and EKS pod identity.

**Synopsis:**
```bash
aws sts assume-role-with-web-identity \
    --role-arn <value> \
    --role-session-name <value> \
    --web-identity-token <value> \
    [--provider-id <value>] \
    [--policy-arns <value>] \
    [--policy <value>] \
    [--duration-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-arn` | **Yes** | string | -- | ARN of the role to assume |
| `--role-session-name` | **Yes** | string | -- | Identifier for the session (2-64 chars) |
| `--web-identity-token` | **Yes** | string | -- | OIDC ID token from the identity provider. Use `file://` for file input |
| `--provider-id` | No | string | None | Fully qualified host of the OIDC identity provider (e.g., `accounts.google.com`) |
| `--policy-arns` | No | list | None | ARNs of managed policies for session policies (max 10). Shorthand: `arn=string ...` |
| `--policy` | No | string | None | Inline JSON session policy (max 2048 packed chars) |
| `--duration-seconds` | No | integer | 3600 | Session duration in seconds (900-43200, limited by role's MaxSessionDuration) |

**Output Schema:**
```json
{
    "Credentials": {
        "AccessKeyId": "string",
        "SecretAccessKey": "string",
        "SessionToken": "string",
        "Expiration": "timestamp"
    },
    "SubjectFromWebIdentityToken": "string",
    "AssumedRoleUser": {
        "AssumedRoleId": "string",
        "Arn": "string"
    },
    "PackedPolicySize": "integer",
    "Provider": "string",
    "Audience": "string",
    "SourceIdentity": "string"
}
```
