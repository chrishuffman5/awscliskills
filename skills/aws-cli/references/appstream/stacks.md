# Stacks

### 2.1 `create-stack`

Creates a new stack for streaming applications.

**Synopsis:**
```bash
aws appstream create-stack \
    --name <value> \
    [--description <value>] \
    [--display-name <value>] \
    [--storage-connectors <value>] \
    [--redirect-url <value>] \
    [--feedback-url <value>] \
    [--user-settings <value>] \
    [--application-settings <value>] \
    [--streaming-experience-settings <value>] \
    [--embed-host-domains <value>] \
    [--access-endpoints <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Unique name for the stack |
| `--description` | No | string | -- | Description of the stack |
| `--display-name` | No | string | -- | Display name |
| `--storage-connectors` | No | list | -- | Storage connectors. Shorthand: `ConnectorType=HOMEFOLDERS\|GOOGLE_DRIVE\|ONE_DRIVE,ResourceIdentifier=string,Domains=string,string` |
| `--redirect-url` | No | string | -- | URL to redirect after streaming session |
| `--feedback-url` | No | string | -- | URL for user feedback |
| `--user-settings` | No | list | -- | User settings. Shorthand: `Action=CLIPBOARD_COPY_FROM_LOCAL_DEVICE\|CLIPBOARD_COPY_TO_LOCAL_DEVICE\|FILE_UPLOAD\|FILE_DOWNLOAD\|PRINTING_TO_LOCAL_DEVICE\|DOMAIN_PASSWORD_SIGNIN\|DOMAIN_SMART_CARD_SIGNIN,Permission=ENABLED\|DISABLED,MaximumLength=integer` |
| `--application-settings` | No | structure | -- | Application settings persistence. Shorthand: `Enabled=boolean,SettingsGroup=string` |
| `--streaming-experience-settings` | No | structure | -- | Streaming experience settings. Shorthand: `PreferredProtocol=TCP\|UDP` |
| `--embed-host-domains` | No | list(string) | -- | Domains for embedding streaming sessions |
| `--access-endpoints` | No | list | -- | Access endpoints. Shorthand: `EndpointType=STREAMING,VpceId=string` |
| `--tags` | No | map | -- | Tags as key-value pairs |

**Output Schema:**
```json
{
    "Stack": {
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "DisplayName": "string",
        "CreatedTime": "timestamp",
        "StorageConnectors": [
            {
                "ConnectorType": "HOMEFOLDERS|GOOGLE_DRIVE|ONE_DRIVE",
                "ResourceIdentifier": "string",
                "Domains": ["string"]
            }
        ],
        "RedirectURL": "string",
        "FeedbackURL": "string",
        "StackErrors": [
            {
                "ErrorCode": "STORAGE_CONNECTOR_ERROR|INTERNAL_SERVICE_ERROR",
                "ErrorMessage": "string"
            }
        ],
        "UserSettings": [
            {
                "Action": "string",
                "Permission": "ENABLED|DISABLED",
                "MaximumLength": "integer"
            }
        ],
        "ApplicationSettings": {
            "Enabled": "boolean",
            "SettingsGroup": "string",
            "S3BucketName": "string"
        },
        "StreamingExperienceSettings": {
            "PreferredProtocol": "TCP|UDP"
        },
        "AccessEndpoints": [
            {
                "EndpointType": "STREAMING",
                "VpceId": "string"
            }
        ],
        "EmbedHostDomains": ["string"]
    }
}
```

---

### 2.2 `delete-stack`

Deletes the specified stack. All associated fleets must be disassociated first.

**Synopsis:**
```bash
aws appstream delete-stack \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the stack to delete |

**Output Schema:**
```json
{}
```

---

### 2.3 `describe-stacks`

Describes one or more stacks.

**Synopsis:**
```bash
aws appstream describe-stacks \
    [--names <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | No | list(string) | -- | Names of the stacks to describe |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "Stacks": [
        {
            "Arn": "string",
            "Name": "string",
            "Description": "string",
            "DisplayName": "string",
            "CreatedTime": "timestamp",
            "StorageConnectors": [],
            "RedirectURL": "string",
            "FeedbackURL": "string",
            "StackErrors": [],
            "UserSettings": [],
            "ApplicationSettings": {},
            "StreamingExperienceSettings": {},
            "AccessEndpoints": [],
            "EmbedHostDomains": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `update-stack`

Updates the specified stack.

**Synopsis:**
```bash
aws appstream update-stack \
    --name <value> \
    [--description <value>] \
    [--display-name <value>] \
    [--storage-connectors <value>] \
    [--redirect-url <value>] \
    [--feedback-url <value>] \
    [--user-settings <value>] \
    [--application-settings <value>] \
    [--streaming-experience-settings <value>] \
    [--embed-host-domains <value>] \
    [--access-endpoints <value>] \
    [--attributes-to-delete <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the stack to update |
| `--description` | No | string | -- | Description |
| `--display-name` | No | string | -- | Display name |
| `--storage-connectors` | No | list | -- | Storage connectors |
| `--redirect-url` | No | string | -- | Redirect URL |
| `--feedback-url` | No | string | -- | Feedback URL |
| `--user-settings` | No | list | -- | User settings |
| `--application-settings` | No | structure | -- | Application settings persistence |
| `--streaming-experience-settings` | No | structure | -- | Streaming experience settings |
| `--embed-host-domains` | No | list(string) | -- | Embed host domains |
| `--access-endpoints` | No | list | -- | Access endpoints |
| `--attributes-to-delete` | No | list(string) | -- | Attributes to delete: `STORAGE_CONNECTORS`, `STORAGE_CONNECTOR_HOMEFOLDERS`, `STORAGE_CONNECTOR_GOOGLE_DRIVE`, `STORAGE_CONNECTOR_ONE_DRIVE`, `REDIRECT_URL`, `FEEDBACK_URL`, `THEME_NAME`, `USER_SETTINGS`, `EMBED_HOST_DOMAINS`, `IAM_ROLE_ARN`, `ACCESS_ENDPOINTS`, `STREAMING_EXPERIENCE_SETTINGS` |

**Output Schema:**
```json
{
    "Stack": {
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "DisplayName": "string",
        "CreatedTime": "timestamp",
        "StorageConnectors": [],
        "RedirectURL": "string",
        "FeedbackURL": "string",
        "StackErrors": [],
        "UserSettings": [],
        "ApplicationSettings": {},
        "AccessEndpoints": [],
        "EmbedHostDomains": ["string"]
    }
}
```

---

### 2.5 `create-streaming-url`

Creates a temporary URL to start a streaming session for the specified user.

**Synopsis:**
```bash
aws appstream create-streaming-url \
    --stack-name <value> \
    --fleet-name <value> \
    --user-id <value> \
    [--application-id <value>] \
    [--validity <value>] \
    [--session-context <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Name of the stack |
| `--fleet-name` | **Yes** | string | -- | Name of the fleet |
| `--user-id` | **Yes** | string | -- | Unique identifier for the user |
| `--application-id` | No | string | -- | Name of the application to launch |
| `--validity` | No | long | 60 | Time in seconds the URL is valid (max 3600) |
| `--session-context` | No | string | -- | Session context passed to the application |

**Output Schema:**
```json
{
    "StreamingURL": "string",
    "Expires": "timestamp"
}
```

---

### 2.6 `describe-sessions`

Describes the streaming sessions for the specified stack and fleet.

**Synopsis:**
```bash
aws appstream describe-sessions \
    --stack-name <value> \
    --fleet-name <value> \
    [--user-id <value>] \
    [--authentication-type <value>] \
    [--instance-id <value>] \
    [--limit <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Name of the stack |
| `--fleet-name` | **Yes** | string | -- | Name of the fleet |
| `--user-id` | No | string | -- | User identifier to filter by |
| `--authentication-type` | No | string | -- | Authentication type: `API`, `SAML`, `USERPOOL`, `AWS_AD` |
| `--instance-id` | No | string | -- | Instance ID to filter by |
| `--limit` | No | integer | -- | Maximum number of results |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "Sessions": [
        {
            "Id": "string",
            "UserId": "string",
            "StackName": "string",
            "FleetName": "string",
            "State": "ACTIVE|PENDING|EXPIRED",
            "ConnectionState": "CONNECTED|NOT_CONNECTED",
            "StartTime": "timestamp",
            "MaxExpirationTime": "timestamp",
            "AuthenticationType": "API|SAML|USERPOOL|AWS_AD",
            "NetworkAccessConfiguration": {
                "EniPrivateIpAddress": "string",
                "EniId": "string"
            },
            "InstanceId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.7 `expire-session`

Immediately stops the specified streaming session.

**Synopsis:**
```bash
aws appstream expire-session \
    --session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Identifier of the streaming session |

**Output Schema:**
```json
{}
```
