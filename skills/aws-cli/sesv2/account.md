# Account

### 8.1 `get-account`

Gets information about the SES account, including sending limits, production access status, and enforcement status.

**Synopsis:**
```bash
aws sesv2 get-account \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No required or optional parameters (beyond global options).

**Output Schema:**
```json
{
    "DedicatedIpAutoWarmupEnabled": true,
    "EnforcementStatus": "string",
    "ProductionAccessEnabled": true,
    "SendQuota": {
        "Max24HourSend": "double",
        "MaxSendRate": "double",
        "SentLast24Hours": "double"
    },
    "SendingEnabled": true,
    "SuppressionAttributes": {
        "SuppressedReasons": ["BOUNCE", "COMPLAINT"]
    },
    "Details": {
        "MailType": "MARKETING|TRANSACTIONAL",
        "WebsiteURL": "string",
        "ContactLanguage": "EN|JA",
        "UseCaseDescription": "string",
        "AdditionalContactEmailAddresses": ["string"],
        "ReviewDetails": {
            "Status": "PENDING|FAILED|GRANTED|DENIED",
            "CaseId": "string"
        }
    },
    "VdmAttributes": {
        "VdmEnabled": "ENABLED|DISABLED",
        "DashboardAttributes": {
            "EngagementMetrics": "ENABLED|DISABLED"
        },
        "GuardianAttributes": {
            "OptimizedSharedDelivery": "ENABLED|DISABLED"
        }
    }
}
```

---

### 8.2 `put-account-details`

Updates the details of your SES account, including mail type, website URL, and use case description. Used when requesting production access.

**Synopsis:**
```bash
aws sesv2 put-account-details \
    --mail-type <value> \
    --website-url <value> \
    --use-case-description <value> \
    [--contact-language <value>] \
    [--additional-contact-email-addresses <value>] \
    [--production-access-enabled | --no-production-access-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--mail-type` | **Yes** | string | -- | Type of email: `MARKETING` or `TRANSACTIONAL` |
| `--website-url` | **Yes** | string | -- | URL of the website associated with your account |
| `--use-case-description` | **Yes** | string | -- | Description of how you plan to use SES |
| `--contact-language` | No | string | `EN` | Preferred contact language: `EN` or `JA` |
| `--additional-contact-email-addresses` | No | list(string) | None | Additional email addresses for account notifications |
| `--production-access-enabled` | No | boolean | -- | Request production access |

**Output Schema:**
```json
{}
```

---

### 8.3 `put-account-dedicated-ip-warmup-attributes`

Enables or disables automatic warmup for dedicated IP addresses in your account.

**Synopsis:**
```bash
aws sesv2 put-account-dedicated-ip-warmup-attributes \
    [--auto-warmup-enabled | --no-auto-warmup-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-warmup-enabled` | No | boolean | true | Enable automatic IP warmup |
| `--no-auto-warmup-enabled` | No | boolean | -- | Disable automatic IP warmup |

**Output Schema:**
```json
{}
```

---

### 8.4 `put-account-sending-attributes`

Enables or disables the ability to send email for the entire account.

**Synopsis:**
```bash
aws sesv2 put-account-sending-attributes \
    [--sending-enabled | --no-sending-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sending-enabled` | No | boolean | false | Enable email sending for the account |
| `--no-sending-enabled` | No | boolean | -- | Disable email sending for the account |

**Output Schema:**
```json
{}
```

---

### 8.5 `put-account-vdm-attributes`

Configures Virtual Deliverability Manager (VDM) settings at the account level, including engagement tracking and optimized shared delivery.

**Synopsis:**
```bash
aws sesv2 put-account-vdm-attributes \
    --vdm-attributes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vdm-attributes` | **Yes** | structure | -- | VDM configuration |

**VDM Attributes Structure:**
```json
{
    "VdmEnabled": "ENABLED|DISABLED",
    "DashboardAttributes": {
        "EngagementMetrics": "ENABLED|DISABLED"
    },
    "GuardianAttributes": {
        "OptimizedSharedDelivery": "ENABLED|DISABLED"
    }
}
```

**Output Schema:**
```json
{}
```

---

### 8.6 `get-domain-statistics-report`

Retrieves engagement and deliverability metrics for a specific domain over a date range.

**Synopsis:**
```bash
aws sesv2 get-domain-statistics-report \
    --domain <value> \
    --start-date <value> \
    --end-date <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain to get statistics for |
| `--start-date` | **Yes** | timestamp | -- | Start of the date range (ISO 8601) |
| `--end-date` | **Yes** | timestamp | -- | End of the date range (ISO 8601) |

**Output Schema:**
```json
{
    "OverallVolume": {
        "VolumeStatistics": {
            "InboxRawCount": "long",
            "SpamRawCount": "long",
            "ProjectedInbox": "long",
            "ProjectedSpam": "long"
        },
        "ReadRatePercent": "double",
        "DomainIspPlacements": [
            {
                "IspName": "string",
                "InboxRawCount": "long",
                "SpamRawCount": "long",
                "InboxPercentage": "double",
                "SpamPercentage": "double"
            }
        ]
    },
    "DailyVolumes": [
        {
            "StartDate": "timestamp",
            "VolumeStatistics": {
                "InboxRawCount": "long",
                "SpamRawCount": "long",
                "ProjectedInbox": "long",
                "ProjectedSpam": "long"
            },
            "DomainIspPlacements": []
        }
    ]
}
```

---

### 8.7 `list-domain-deliverability-campaigns`

Lists deliverability campaigns that were detected for a specific domain during a date range. Requires the deliverability dashboard to be enabled.

**Synopsis:**
```bash
aws sesv2 list-domain-deliverability-campaigns \
    --start-date <value> \
    --end-date <value> \
    --subscribed-domain <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-date` | **Yes** | timestamp | -- | Start of the date range (ISO 8601) |
| `--end-date` | **Yes** | timestamp | -- | End of the date range (ISO 8601) |
| `--subscribed-domain` | **Yes** | string | -- | Domain subscribed for deliverability insights |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DomainDeliverabilityCampaigns": [
        {
            "CampaignId": "string",
            "ImageUrl": "string",
            "Subject": "string",
            "FromAddress": "string",
            "SendingIps": ["string"],
            "FirstSeenDateTime": "timestamp",
            "LastSeenDateTime": "timestamp",
            "InboxCount": "long",
            "SpamCount": "long",
            "ReadRate": "double",
            "DeleteRate": "double",
            "ReadDeleteRate": "double",
            "ProjectedVolume": "long",
            "Esps": ["string"]
        }
    ],
    "NextToken": "string"
}
```
