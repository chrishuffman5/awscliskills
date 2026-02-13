# Users & Groups

### 11.1 `register-user`

Registers a new QuickSight user.

**Synopsis:**
```bash
aws quicksight register-user \
    --aws-account-id <value> \
    --namespace <value> \
    --identity-type <value> \
    --email <value> \
    --user-role <value> \
    [--iam-arn <value>] \
    [--session-name <value>] \
    [--user-name <value>] \
    [--custom-permissions-name <value>] \
    [--external-login-federation-provider-type <value>] \
    [--custom-federation-provider-url <value>] \
    [--external-login-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--namespace` | **Yes** | string | -- | Namespace (usually `default`) |
| `--identity-type` | **Yes** | string | -- | `IAM`, `QUICKSIGHT`, or `IAM_IDENTITY_CENTER` |
| `--email` | **Yes** | string | -- | Email address |
| `--user-role` | **Yes** | string | -- | `ADMIN`, `AUTHOR`, `READER`, `ADMIN_PRO`, `AUTHOR_PRO`, `READER_PRO` |
| `--iam-arn` | No | string | None | IAM user/role ARN (required for IAM identity type) |
| `--session-name` | No | string | None | Session name for IAM role federation |
| `--user-name` | No | string | None | QuickSight user name |
| `--custom-permissions-name` | No | string | None | Custom permissions profile name |
| `--tags` | No | list | None | Resource tags |

**Output Schema:**
```json
{
    "User": {
        "Arn": "string",
        "UserName": "string",
        "Email": "string",
        "Role": "ADMIN|AUTHOR|READER|ADMIN_PRO|AUTHOR_PRO|READER_PRO",
        "IdentityType": "IAM|QUICKSIGHT|IAM_IDENTITY_CENTER",
        "Active": "boolean",
        "PrincipalId": "string",
        "CustomPermissionsName": "string",
        "ExternalLoginFederationProviderType": "string",
        "ExternalLoginFederationProviderUrl": "string",
        "ExternalLoginId": "string"
    },
    "UserInvitationUrl": "string",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 11.2 `describe-user`

Describes a QuickSight user.

**Synopsis:**
```bash
aws quicksight describe-user \
    --aws-account-id <value> \
    --namespace <value> \
    --user-name <value>
```

---

### 11.3 `update-user`

Updates a user's role, email, or custom permissions.

**Synopsis:**
```bash
aws quicksight update-user \
    --aws-account-id <value> \
    --namespace <value> \
    --user-name <value> \
    --email <value> \
    --role <value> \
    [--custom-permissions-name <value>] \
    [--unapply-custom-permissions | --no-unapply-custom-permissions] \
    [--external-login-federation-provider-type <value>] \
    [--custom-federation-provider-url <value>] \
    [--external-login-id <value>]
```

---

### 11.4 `delete-user` / `delete-user-by-principal-id`

Delete a user by name or principal ID.

**Synopsis:**
```bash
aws quicksight delete-user \
    --aws-account-id <value> --namespace <value> --user-name <value>

aws quicksight delete-user-by-principal-id \
    --aws-account-id <value> --namespace <value> --principal-id <value>
```

---

### 11.5 `list-users`

Lists all users in a namespace. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-users \
    --aws-account-id <value> \
    --namespace <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

---

### 11.6 `create-group`

Creates a group.

**Synopsis:**
```bash
aws quicksight create-group \
    --aws-account-id <value> \
    --namespace <value> \
    --group-name <value> \
    [--description <value>]
```

**Output Schema:**
```json
{
    "Group": {
        "Arn": "string",
        "GroupName": "string",
        "Description": "string",
        "PrincipalId": "string"
    },
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 11.7 `describe-group` / `update-group` / `delete-group`

Manage groups.

**Synopsis:**
```bash
aws quicksight describe-group --aws-account-id <value> --namespace <value> --group-name <value>
aws quicksight update-group --aws-account-id <value> --namespace <value> --group-name <value> [--description <value>]
aws quicksight delete-group --aws-account-id <value> --namespace <value> --group-name <value>
```

---

### 11.8 `list-groups` / `search-groups`

List or search groups. **Paginated operations.**

**Synopsis:**
```bash
aws quicksight list-groups --aws-account-id <value> --namespace <value>
aws quicksight search-groups --aws-account-id <value> --namespace <value> --filters <value>
```

---

### 11.9 `create-group-membership` / `describe-group-membership` / `delete-group-membership`

Manage group memberships.

**Synopsis:**
```bash
aws quicksight create-group-membership \
    --aws-account-id <value> --namespace <value> \
    --group-name <value> --member-name <value>

aws quicksight delete-group-membership \
    --aws-account-id <value> --namespace <value> \
    --group-name <value> --member-name <value>
```

---

### 11.10 `list-group-memberships` / `list-user-groups`

List group members or a user's groups. **Paginated operations.**

**Synopsis:**
```bash
aws quicksight list-group-memberships --aws-account-id <value> --namespace <value> --group-name <value>
aws quicksight list-user-groups --aws-account-id <value> --namespace <value> --user-name <value>
```
