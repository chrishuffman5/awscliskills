# Account & Reporting

### 19.1 `get-account-summary`

Retrieves account-level usage numbers (users, groups, roles, policies, MFA devices, etc.).

**Synopsis:**
```bash
aws iam get-account-summary
```

**Output Schema:**
```json
{
    "SummaryMap": {
        "Users": integer,
        "UsersQuota": integer,
        "Groups": integer,
        "GroupsQuota": integer,
        "Roles": integer,
        "RolesQuota": integer,
        "Policies": integer,
        "PoliciesQuota": integer,
        "AccountMFAEnabled": integer,
        "MFADevices": integer,
        "MFADevicesInUse": integer,
        "AccessKeysPerUserQuota": integer,
        "ServerCertificates": integer,
        "ServerCertificatesQuota": integer
    }
}
```

---

### 19.2 `get-account-authorization-details`

Retrieves all users, groups, roles, and policies in the account. **Paginated.**

**Synopsis:**
```bash
aws iam get-account-authorization-details \
    [--filter <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | list(string) | all | `User`, `Role`, `Group`, `LocalManagedPolicy`, `AWSManagedPolicy` |

**Output Schema:**
```json
{
    "UserDetailList": [
        {
            "UserName": "string",
            "UserId": "string",
            "Arn": "string",
            "Path": "string",
            "CreateDate": "timestamp",
            "GroupList": ["string"],
            "AttachedManagedPolicies": [{ "PolicyName": "string", "PolicyArn": "string" }],
            "UserPolicyList": [{ "PolicyName": "string", "PolicyDocument": "string" }]
        }
    ],
    "GroupDetailList": [
        {
            "GroupName": "string",
            "GroupId": "string",
            "Arn": "string",
            "Path": "string",
            "CreateDate": "timestamp",
            "AttachedManagedPolicies": [{ "PolicyName": "string", "PolicyArn": "string" }],
            "GroupPolicyList": [{ "PolicyName": "string", "PolicyDocument": "string" }]
        }
    ],
    "RoleDetailList": [
        {
            "RoleName": "string",
            "RoleId": "string",
            "Arn": "string",
            "Path": "string",
            "CreateDate": "timestamp",
            "AssumeRolePolicyDocument": "string",
            "AttachedManagedPolicies": [{ "PolicyName": "string", "PolicyArn": "string" }],
            "RolePolicyList": [{ "PolicyName": "string", "PolicyDocument": "string" }],
            "InstanceProfileList": [{ "InstanceProfileName": "string", "Arn": "string" }]
        }
    ],
    "Policies": [
        {
            "PolicyName": "string",
            "PolicyId": "string",
            "Arn": "string",
            "DefaultVersionId": "string",
            "AttachmentCount": integer,
            "IsAttachable": true|false,
            "PolicyVersionList": [
                {
                    "Document": "string",
                    "VersionId": "string",
                    "IsDefaultVersion": true|false,
                    "CreateDate": "timestamp"
                }
            ]
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 19.3 `generate-credential-report`

Generates a credential report for the account. Takes a few seconds.

**Synopsis:**
```bash
aws iam generate-credential-report
```

**Output Schema:**
```json
{
    "State": "STARTED|INPROGRESS|COMPLETE",
    "Description": "string"
}
```

---

### 19.4 `get-credential-report`

Retrieves the credential report (CSV, base64-encoded).

**Synopsis:**
```bash
aws iam get-credential-report
```

**Output Schema:**
```json
{
    "Content": "blob (base64-encoded CSV)",
    "ReportFormat": "text/csv",
    "GeneratedTime": "timestamp"
}
```

---

### 19.5 `get-account-password-policy`

Retrieves the account password policy.

**Synopsis:**
```bash
aws iam get-account-password-policy
```

**Output Schema:**
```json
{
    "PasswordPolicy": {
        "MinimumPasswordLength": integer,
        "RequireSymbols": true|false,
        "RequireNumbers": true|false,
        "RequireUppercaseCharacters": true|false,
        "RequireLowercaseCharacters": true|false,
        "AllowUsersToChangePassword": true|false,
        "ExpirePasswords": true|false,
        "MaxPasswordAge": integer,
        "PasswordReusePrevention": integer,
        "HardExpiry": true|false
    }
}
```

---

### 19.6 `update-account-password-policy`

Sets the account-wide password policy for IAM users.

**Synopsis:**
```bash
aws iam update-account-password-policy \
    [--minimum-password-length <value>] \
    [--require-symbols | --no-require-symbols] \
    [--require-numbers | --no-require-numbers] \
    [--require-uppercase-characters | --no-require-uppercase-characters] \
    [--require-lowercase-characters | --no-require-lowercase-characters] \
    [--allow-users-to-change-password | --no-allow-users-to-change-password] \
    [--max-password-age <value>] \
    [--password-reuse-prevention <value>] \
    [--hard-expiry | --no-hard-expiry]
```

**Output:** None on success.

---

### 19.7 `delete-account-password-policy`

Deletes the account password policy (reverts to defaults).

**Synopsis:**
```bash
aws iam delete-account-password-policy
```

**Output:** None on success.

---

### 19.8 `create-account-alias`

Creates an alias for the AWS account (used in console login URL).

**Synopsis:**
```bash
aws iam create-account-alias --account-alias <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-alias` | **Yes** | string | -- | Alias name (3-63 chars, lowercase alphanumeric + hyphens) |

**Output:** None on success.

---

### 19.9 `list-account-aliases`

Lists the account aliases. **Paginated.**

**Synopsis:**
```bash
aws iam list-account-aliases [--starting-token <value>] [--max-items <value>]
```

**Output Schema:**
```json
{
    "AccountAliases": ["string"],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 19.10 `delete-account-alias`

Deletes the account alias.

**Synopsis:**
```bash
aws iam delete-account-alias --account-alias <value>
```

**Output:** None on success.

---

### 19.11 `generate-service-last-accessed-details`

Generates a report about when services were last accessed by an IAM entity.

**Synopsis:**
```bash
aws iam generate-service-last-accessed-details --arn <value> [--granularity <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the IAM entity (user, group, role, or policy) |
| `--granularity` | No | string | `SERVICE_LEVEL` | `SERVICE_LEVEL` or `ACTION_LEVEL` |

**Output Schema:**
```json
{
    "JobId": "string"
}
```

---

### 19.12 `get-service-last-accessed-details`

Retrieves the service last accessed report generated by `generate-service-last-accessed-details`. **Paginated.**

**Synopsis:**
```bash
aws iam get-service-last-accessed-details --job-id <value> [--max-items <value>] [--starting-token <value>]
```

**Output Schema:**
```json
{
    "JobStatus": "IN_PROGRESS|COMPLETED|FAILED",
    "JobType": "SERVICE_LEVEL|ACTION_LEVEL",
    "JobCreationDate": "timestamp",
    "JobCompletionDate": "timestamp",
    "ServicesLastAccessed": [
        {
            "ServiceName": "string",
            "ServiceNamespace": "string",
            "LastAuthenticated": "timestamp",
            "LastAuthenticatedEntity": "string",
            "LastAuthenticatedRegion": "string",
            "TotalAuthenticatedEntities": integer
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 19.13 `get-service-last-accessed-details-with-entities`

Retrieves entities that last accessed a specific service. **Paginated.**

**Synopsis:**
```bash
aws iam get-service-last-accessed-details-with-entities \
    --job-id <value> \
    --service-namespace <value> \
    [--max-items <value>] \
    [--starting-token <value>]
```

**Output Schema:**
```json
{
    "JobStatus": "IN_PROGRESS|COMPLETED|FAILED",
    "JobCreationDate": "timestamp",
    "JobCompletionDate": "timestamp",
    "EntityDetailsList": [
        {
            "EntityInfo": {
                "Arn": "string",
                "Name": "string",
                "Type": "USER|ROLE|GROUP",
                "Id": "string",
                "Path": "string"
            },
            "LastAuthenticated": "timestamp"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 19.14 `set-security-token-service-preferences`

Sets the STS global endpoint token version (v1 or v2).

**Synopsis:**
```bash
aws iam set-security-token-service-preferences --global-endpoint-token-version <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-endpoint-token-version` | **Yes** | string | -- | `v1Token` or `v2Token` |

**Output:** None on success.

---

### 19.15 `list-policies-granting-service-access`

Lists policies that grant access to a specific service. Not paginated.

**Synopsis:**
```bash
aws iam list-policies-granting-service-access \
    --arn <value> \
    --service-namespaces <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the IAM identity |
| `--service-namespaces` | **Yes** | list(string) | -- | Service namespaces (e.g., `iam`, `ec2`, `s3`). Max 200 |

**Output Schema:**
```json
{
    "PoliciesGrantingServiceAccess": [
        {
            "ServiceNamespace": "string",
            "Policies": [
                {
                    "PolicyName": "string",
                    "PolicyType": "INLINE|MANAGED",
                    "PolicyArn": "string",
                    "EntityType": "USER|ROLE|GROUP",
                    "EntityName": "string"
                }
            ]
        }
    ],
    "IsTruncated": true|false
}
```

---
