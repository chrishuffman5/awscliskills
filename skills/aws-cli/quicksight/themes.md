# Themes

### 6.1 `create-theme`

Creates a custom theme for QuickSight dashboards and analyses.

**Synopsis:**
```bash
aws quicksight create-theme \
    --aws-account-id <value> \
    --theme-id <value> \
    --name <value> \
    --base-theme-id <value> \
    --configuration <value> \
    [--permissions <value>] \
    [--tags <value>] \
    [--version-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--theme-id` | **Yes** | string | -- | Theme ID (1-512 chars) |
| `--name` | **Yes** | string | -- | Display name (1-2048 chars) |
| `--base-theme-id` | **Yes** | string | -- | ID of the theme to extend |
| `--configuration` | **Yes** | structure | -- | Theme configuration (colors, typography, etc.) |
| `--permissions` | No | list | None | Resource permissions |
| `--tags` | No | list | None | Resource tags |
| `--version-description` | No | string | None | Version description |

**Output Schema:**
```json
{
    "Arn": "string",
    "VersionArn": "string",
    "ThemeId": "string",
    "CreationStatus": "string",
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 6.2 `describe-theme`

Describes a theme.

**Synopsis:**
```bash
aws quicksight describe-theme \
    --aws-account-id <value> \
    --theme-id <value> \
    [--version-number <value>] \
    [--alias-name <value>]
```

---

### 6.3 `update-theme`

Updates a theme (creates new version).

**Synopsis:**
```bash
aws quicksight update-theme \
    --aws-account-id <value> \
    --theme-id <value> \
    --name <value> \
    --base-theme-id <value> \
    [--configuration <value>] \
    [--version-description <value>]
```

---

### 6.4 `delete-theme`

Deletes a theme.

**Synopsis:**
```bash
aws quicksight delete-theme \
    --aws-account-id <value> \
    --theme-id <value> \
    [--version-number <value>]
```

---

### 6.5 `list-themes` / `list-theme-versions`

List themes or theme versions. **Paginated operations.**

**Synopsis:**
```bash
aws quicksight list-themes --aws-account-id <value> [--type QUICKSIGHT|CUSTOM|ALL]
aws quicksight list-theme-versions --aws-account-id <value> --theme-id <value>
```

---

### 6.6 `describe-theme-permissions` / `update-theme-permissions`

Manage theme permissions.

**Synopsis:**
```bash
aws quicksight describe-theme-permissions \
    --aws-account-id <value> --theme-id <value>

aws quicksight update-theme-permissions \
    --aws-account-id <value> --theme-id <value> \
    [--grant-permissions <value>] [--revoke-permissions <value>]
```

---

### 6.7 `create-theme-alias` / `describe-theme-alias` / `update-theme-alias` / `delete-theme-alias` / `list-theme-aliases`

Manage theme aliases. Same pattern as template aliases.

**Synopsis:**
```bash
aws quicksight create-theme-alias \
    --aws-account-id <value> --theme-id <value> \
    --alias-name <value> --theme-version-number <value>

aws quicksight list-theme-aliases \
    --aws-account-id <value> --theme-id <value>
```
