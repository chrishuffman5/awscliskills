# Custom Permissions

Custom permissions allow defining fine-grained permission profiles that can be assigned to users and roles.

### 19.1 `create-custom-permissions`

Creates a custom permissions profile.

**Synopsis:**
```bash
aws quicksight create-custom-permissions \
    --aws-account-id <value> \
    --custom-permissions-name <value> \
    [--capabilities <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--custom-permissions-name` | **Yes** | string | -- | Name for the custom permissions profile |
| `--capabilities` | No | structure | None | Capability restrictions |
| `--tags` | No | list | None | Resource tags |

**Output Schema:**
```json
{
    "Arn": "string",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 19.2 `describe-custom-permissions` / `update-custom-permissions` / `delete-custom-permissions`

Manage custom permissions.

**Synopsis:**
```bash
aws quicksight describe-custom-permissions --aws-account-id <value> --custom-permissions-name <value>
aws quicksight update-custom-permissions --aws-account-id <value> --custom-permissions-name <value> --capabilities <value>
aws quicksight delete-custom-permissions --aws-account-id <value> --custom-permissions-name <value>
```

---

### 19.3 `list-custom-permissions`

Lists custom permissions profiles. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-custom-permissions \
    --aws-account-id <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

---

### 19.4 `describe-account-custom-permission` / `update-account-custom-permission` / `delete-account-custom-permission`

Manage the default custom permissions for the account.

**Synopsis:**
```bash
aws quicksight describe-account-custom-permission --aws-account-id <value>
aws quicksight update-account-custom-permission --aws-account-id <value> --custom-permissions-name <value>
aws quicksight delete-account-custom-permission --aws-account-id <value>
```

---

### 19.5 `describe-role-custom-permission` / `update-role-custom-permission` / `delete-role-custom-permission`

Manage custom permissions for a specific role.

**Synopsis:**
```bash
aws quicksight describe-role-custom-permission \
    --aws-account-id <value> --namespace <value> --role <value>
aws quicksight update-role-custom-permission \
    --aws-account-id <value> --namespace <value> --role <value> --custom-permissions-name <value>
aws quicksight delete-role-custom-permission \
    --aws-account-id <value> --namespace <value> --role <value>
```

---

### 19.6 `update-user-custom-permission` / `delete-user-custom-permission`

Manage custom permissions for a specific user.

**Synopsis:**
```bash
aws quicksight update-user-custom-permission \
    --aws-account-id <value> --namespace <value> --user-name <value> --custom-permissions-name <value>
aws quicksight delete-user-custom-permission \
    --aws-account-id <value> --namespace <value> --user-name <value>
```
