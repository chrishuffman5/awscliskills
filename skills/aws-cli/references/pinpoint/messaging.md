# Messaging

### 8.1 `send-messages`

Sends a direct message to one or more addresses or endpoints.

**Synopsis:**
```bash
aws pinpoint send-messages \
    --application-id <value> \
    --message-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--message-request` | **Yes** | structure | -- | Message configuration (JSON recommended, or `file://path.json`) |

**MessageRequest Key Fields:**
- `Addresses` (map): Map of address -> AddressConfiguration (ChannelType, BodyOverride, TitleOverride, Substitutions, Context, RawContent)
- `Endpoints` (map): Map of endpoint ID -> EndpointSendConfiguration
- `MessageConfiguration` (structure, **required**): Channel-specific messages
- `TemplateConfiguration` (structure): Template references
- `Context` (map): Custom attributes
- `TraceId` (string): Trace identifier

**MessageConfiguration Channels:**
- `SMSMessage`: `Body`, `MessageType` (`TRANSACTIONAL|PROMOTIONAL`), `OriginationNumber`, `SenderId`, `Keyword`, `EntityId`, `TemplateId`
- `EmailMessage`: `FromAddress`, `SimpleEmail` (Subject, HtmlPart, TextPart), `RawEmail`, `FeedbackForwardingAddress`, `ReplyToAddresses`, `Headers`
- `GCMMessage`/`APNSMessage`/`ADMMessage`/`BaiduMessage`: `Body`, `Title`, `Action` (`OPEN_APP|DEEP_LINK|URL`), `Url`, `Sound`, `SilentPush`, `Data`, `TimeToLive`
- `VoiceMessage`: `Body`, `LanguageCode`, `OriginationNumber`, `VoiceId`
- `DefaultMessage`: `Body`, `Substitutions`

**Output Schema:**
```json
{
    "MessageResponse": {
        "ApplicationId": "string",
        "RequestId": "string",
        "Result": {
            "address": {
                "DeliveryStatus": "SUCCESSFUL|THROTTLED|TEMPORARY_FAILURE|PERMANENT_FAILURE|UNKNOWN_FAILURE|OPT_OUT|DUPLICATE",
                "MessageId": "string",
                "StatusCode": "integer",
                "StatusMessage": "string",
                "UpdatedToken": "string"
            }
        },
        "EndpointResult": {}
    }
}
```

---

### 8.2 `send-users-messages`

Sends a message to all endpoints associated with specific user IDs.

**Synopsis:**
```bash
aws pinpoint send-users-messages \
    --application-id <value> \
    --send-users-message-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--send-users-message-request` | **Yes** | structure | -- | User-targeted message configuration |

**SendUsersMessageRequest Key Fields:**
- `Users` (map, **required**): Map of user ID -> EndpointSendConfiguration
- `MessageConfiguration` (structure, **required**): Channel-specific messages
- `TemplateConfiguration` (structure): Template references
- `Context` (map): Custom attributes
- `TraceId` (string): Trace identifier

**Output Schema:**
```json
{
    "SendUsersMessageResponse": {
        "ApplicationId": "string",
        "RequestId": "string",
        "Result": {
            "userId": {
                "endpointId": {
                    "DeliveryStatus": "string",
                    "MessageId": "string",
                    "StatusCode": "integer",
                    "StatusMessage": "string"
                }
            }
        }
    }
}
```

---

### 8.3 `send-otp-message`

Sends a one-time password (OTP) message.

**Synopsis:**
```bash
aws pinpoint send-otp-message \
    --application-id <value> \
    --send-otp-message-request-parameters <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--send-otp-message-request-parameters` | **Yes** | structure | -- | OTP configuration |

**Request Fields:**
- `BrandName` (string, **required**): Brand name in the OTP message
- `Channel` (string, **required**): `SMS` or `VOICE`
- `DestinationIdentity` (string, **required**): Phone number (E.164)
- `ReferenceId` (string, **required**): Unique reference for this OTP
- `AllowedAttempts` (integer): Max verification attempts (default 5)
- `CodeLength` (integer): OTP code length (default 5)
- `ValidityPeriod` (integer): OTP validity in minutes (default 5)
- `Language` (string): Language for voice OTP
- `OriginationIdentity` (string): Origination number/sender ID
- `EntityId` (string): Entity ID for India
- `TemplateId` (string): Template ID for India

**Output Schema:**
```json
{
    "MessageResponse": {
        "ApplicationId": "string",
        "RequestId": "string",
        "Result": {}
    }
}
```

---

### 8.4 `verify-otp-message`

Verifies an OTP code.

**Synopsis:**
```bash
aws pinpoint verify-otp-message \
    --application-id <value> \
    --verify-otp-message-request-parameters <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--verify-otp-message-request-parameters` | **Yes** | structure | -- | Shorthand: `DestinationIdentity=string,Otp=string,ReferenceId=string` |

**Output Schema:**
```json
{
    "VerificationResponse": {
        "Valid": "boolean"
    }
}
```

---

### 8.5 `put-events`

Records events for endpoints. Used for recording custom events.

**Synopsis:**
```bash
aws pinpoint put-events \
    --application-id <value> \
    --events-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--events-request` | **Yes** | structure | -- | Events batch (JSON recommended) |

**EventsRequest Structure:**
- `BatchItem` (map, **required**): Map of endpoint ID -> EventsBatch containing `Endpoint` (PublicEndpoint) and `Events` (map of event ID -> Event with `EventType`, `Timestamp`, `Attributes`, `Metrics`, `Session`)

**Output Schema:**
```json
{
    "EventsResponse": {
        "Results": {
            "endpointId": {
                "EndpointItemResponse": {"Message": "string", "StatusCode": "integer"},
                "EventsItemResponse": {
                    "eventId": {"Message": "string", "StatusCode": "integer"}
                }
            }
        }
    }
}
```

---

### 8.6 `get-in-app-messages`

Gets in-app messages for an endpoint.

**Synopsis:**
```bash
aws pinpoint get-in-app-messages \
    --application-id <value> \
    --endpoint-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--endpoint-id` | **Yes** | string | -- | Endpoint ID |

**Output Schema:**
```json
{
    "InAppMessagesResponse": {
        "InAppMessageCampaigns": [
            {
                "CampaignId": "string",
                "InAppMessage": {},
                "Priority": "integer",
                "Schedule": {},
                "SessionCap": "integer",
                "DailyCap": "integer",
                "TotalCap": "integer",
                "TreatmentId": "string"
            }
        ]
    }
}
```
