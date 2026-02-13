# Platform Applications

### 5.1 `create-platform-application`

Creates a platform application object for mobile push notifications (APNS, GCM/FCM, ADM).

**Synopsis:**
```bash
aws sns create-platform-application \
    --name <value> \
    --platform <value> \
    --attributes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Application name (1-256 chars). Alphanumeric, hyphens, underscores, periods |
| `--platform` | **Yes** | string | -- | Platform type: `ADM`, `APNS`, `APNS_SANDBOX`, `GCM` |
| `--attributes` | **Yes** | map | -- | Platform credentials (see table below) |

**Platform Credentials:**

| Platform | PlatformPrincipal | PlatformCredential |
|----------|-------------------|-------------------|
| ADM | client id | client secret |
| APNS / APNS_SANDBOX (cert) | SSL certificate | private key |
| APNS / APNS_SANDBOX (token) | signing key ID | signing key |
| GCM (key) | -- | API key |
| GCM (token) | -- | JSON private key file |

**Output Schema:**
```json
{
    "PlatformApplicationArn": "string"
}
```

---

### 5.2 `delete-platform-application`

Deletes a platform application object.

**Synopsis:**
```bash
aws sns delete-platform-application \
    --platform-application-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--platform-application-arn` | **Yes** | string | -- | ARN of the platform application to delete |

**Output Schema:** None

---

### 5.3 `get-platform-application-attributes`

Retrieves the attributes of a platform application object.

**Synopsis:**
```bash
aws sns get-platform-application-attributes \
    --platform-application-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--platform-application-arn` | **Yes** | string | -- | ARN of the platform application |

**Output Schema:**
```json
{
    "Attributes": {
        "Enabled": "true|false",
        "AppleCertificateExpirationDate": "string",
        "ApplePlatformTeamID": "string",
        "ApplePlatformBundleID": "string",
        "EventEndpointCreated": "string (topic ARN)",
        "EventEndpointDeleted": "string (topic ARN)",
        "EventEndpointUpdated": "string (topic ARN)",
        "EventDeliveryFailure": "string (topic ARN)",
        "SuccessFeedbackRoleArn": "string",
        "FailureFeedbackRoleArn": "string",
        "SuccessFeedbackSampleRate": "string"
    }
}
```

---

### 5.4 `set-platform-application-attributes`

Sets the attributes of a platform application object.

**Synopsis:**
```bash
aws sns set-platform-application-attributes \
    --platform-application-arn <value> \
    --attributes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--platform-application-arn` | **Yes** | string | -- | ARN of the platform application |
| `--attributes` | **Yes** | map | -- | Attributes to set. Supported: `PlatformCredential`, `PlatformPrincipal`, `EventEndpointCreated`, `EventEndpointDeleted`, `EventEndpointUpdated`, `EventDeliveryFailure`, `SuccessFeedbackRoleArn`, `FailureFeedbackRoleArn`, `SuccessFeedbackSampleRate` |

**Output Schema:** None

---

### 5.5 `list-platform-applications`

Lists all platform applications. **Paginated operation** (max 100 per page). Rate limit: 15 TPS.

**Synopsis:**
```bash
aws sns list-platform-applications \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--no-paginate] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--max-items` | No | integer | None | Maximum total items to return |

**Output Schema:**
```json
{
    "PlatformApplications": [
        {
            "PlatformApplicationArn": "string",
            "Attributes": {
                "string": "string"
            }
        }
    ],
    "NextToken": "string"
}
```
