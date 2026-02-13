# Embedding

### 15.1 `generate-embed-url-for-registered-user`

Generates an embed URL for a registered QuickSight user. Supports dashboard, visual, console, and Q search bar embedding.

**Synopsis:**
```bash
aws quicksight generate-embed-url-for-registered-user \
    --aws-account-id <value> \
    --user-arn <value> \
    --experience-configuration <value> \
    [--session-lifetime-in-minutes <value>] \
    [--allowed-domains <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--user-arn` | **Yes** | string | -- | QuickSight user ARN |
| `--experience-configuration` | **Yes** | structure | -- | Type of embedding experience |
| `--session-lifetime-in-minutes` | No | long | 600 | Session lifetime (15-600 minutes) |
| `--allowed-domains` | No | list(string) | None | Domains allowed to embed |

**Experience Configuration (one of):**
```json
{
    "Dashboard": {
        "InitialDashboardId": "string",
        "FeatureConfigurations": {}
    }
}
```
```json
{
    "QuickSightConsole": {
        "InitialPath": "string",
        "FeatureConfigurations": {}
    }
}
```
```json
{
    "QSearchBar": {
        "InitialTopicId": "string"
    }
}
```
```json
{
    "DashboardVisual": {
        "InitialDashboardVisualId": {
            "DashboardId": "string",
            "SheetId": "string",
            "VisualId": "string"
        }
    }
}
```

**Output Schema:**
```json
{
    "EmbedUrl": "string",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 15.2 `generate-embed-url-for-registered-user-with-identity`

Same as above but with additional identity context.

**Synopsis:**
```bash
aws quicksight generate-embed-url-for-registered-user-with-identity \
    --aws-account-id <value> \
    --experience-configuration <value> \
    [--session-lifetime-in-minutes <value>] \
    [--allowed-domains <value>]
```

---

### 15.3 `generate-embed-url-for-anonymous-user`

Generates an embed URL for anonymous access (no QuickSight user required).

**Synopsis:**
```bash
aws quicksight generate-embed-url-for-anonymous-user \
    --aws-account-id <value> \
    --namespace <value> \
    --authorized-resource-arns <value> \
    --experience-configuration <value> \
    [--session-lifetime-in-minutes <value>] \
    [--session-tags <value>] \
    [--allowed-domains <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--namespace` | **Yes** | string | -- | Namespace |
| `--authorized-resource-arns` | **Yes** | list(string) | -- | Dashboard ARNs accessible by anonymous user |
| `--experience-configuration` | **Yes** | structure | -- | Embedding experience type |
| `--session-lifetime-in-minutes` | No | long | 600 | Session lifetime (15-600 minutes) |
| `--session-tags` | No | list | None | Session tags for row-level security |
| `--allowed-domains` | No | list(string) | None | Allowed embedding domains |

---

### 15.4 `get-dashboard-embed-url`

Gets a URL for embedding a dashboard (legacy API).

**Synopsis:**
```bash
aws quicksight get-dashboard-embed-url \
    --aws-account-id <value> \
    --dashboard-id <value> \
    --identity-type <value> \
    [--session-lifetime-in-minutes <value>] \
    [--undo-redo-disabled | --no-undo-redo-disabled] \
    [--reset-disabled | --no-reset-disabled] \
    [--state-persistence-enabled | --no-state-persistence-enabled] \
    [--user-arn <value>] \
    [--namespace <value>] \
    [--additional-dashboard-ids <value>]
```

---

### 15.5 `get-session-embed-url`

Gets a URL for embedding the full QuickSight console session (legacy API).

**Synopsis:**
```bash
aws quicksight get-session-embed-url \
    --aws-account-id <value> \
    [--entry-point <value>] \
    [--session-lifetime-in-minutes <value>] \
    [--user-arn <value>]
```
