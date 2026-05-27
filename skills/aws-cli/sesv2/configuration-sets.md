# Configuration Sets

### 2.1 `create-configuration-set`

Creates a configuration set. Configuration sets are groups of rules applied to emails you send, such as event publishing destinations, IP pool assignments, and sending controls.

**Synopsis:**
```bash
aws sesv2 create-configuration-set \
    --configuration-set-name <value> \
    [--tracking-options <value>] \
    [--delivery-options <value>] \
    [--reputation-options <value>] \
    [--sending-options <value>] \
    [--tags <value>] \
    [--suppression-options <value>] \
    [--vdm-options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-set-name` | **Yes** | string | -- | Name of the configuration set |
| `--tracking-options` | No | structure | None | Custom redirect domain for open/click tracking. Shorthand: `CustomRedirectDomain=string` |
| `--delivery-options` | No | structure | None | Delivery options including TLS policy and sending pool |
| `--reputation-options` | No | structure | None | Reputation metric tracking. Shorthand: `ReputationMetricsEnabled=boolean,LastFreshStart=timestamp` |
| `--sending-options` | No | structure | None | Sending enabled flag. Shorthand: `SendingEnabled=boolean` |
| `--tags` | No | list | None | Tags to apply. Shorthand: `Key=string,Value=string ...` |
| `--suppression-options` | No | structure | None | Suppression list reasons. Shorthand: `SuppressedReasons=BOUNCE,COMPLAINT` |
| `--vdm-options` | No | structure | None | Virtual Deliverability Manager options |

**Delivery Options Structure:**
```json
{
    "TlsPolicy": "REQUIRE|OPTIONAL",
    "SendingPoolName": "string"
}
```

**VDM Options Structure:**
```json
{
    "DashboardOptions": {
        "EngagementMetrics": "ENABLED|DISABLED"
    },
    "GuardianOptions": {
        "OptimizedSharedDelivery": "ENABLED|DISABLED"
    }
}
```

**Output Schema:**
```json
{}
```

---

### 2.2 `delete-configuration-set`

Deletes a configuration set. All event destinations associated with the configuration set are also deleted.

**Synopsis:**
```bash
aws sesv2 delete-configuration-set \
    --configuration-set-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-set-name` | **Yes** | string | -- | Name of the configuration set to delete |

**Output Schema:**
```json
{}
```

---

### 2.3 `get-configuration-set`

Gets information about an existing configuration set, including delivery options, reputation options, sending options, and tracking options.

**Synopsis:**
```bash
aws sesv2 get-configuration-set \
    --configuration-set-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-set-name` | **Yes** | string | -- | Name of the configuration set |

**Output Schema:**
```json
{
    "ConfigurationSetName": "string",
    "TrackingOptions": {
        "CustomRedirectDomain": "string"
    },
    "DeliveryOptions": {
        "TlsPolicy": "REQUIRE|OPTIONAL",
        "SendingPoolName": "string"
    },
    "ReputationOptions": {
        "ReputationMetricsEnabled": true|false,
        "LastFreshStart": "timestamp"
    },
    "SendingOptions": {
        "SendingEnabled": true|false
    },
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "SuppressionOptions": {
        "SuppressedReasons": ["BOUNCE"|"COMPLAINT"]
    },
    "VdmOptions": {
        "DashboardOptions": {
            "EngagementMetrics": "ENABLED|DISABLED"
        },
        "GuardianOptions": {
            "OptimizedSharedDelivery": "ENABLED|DISABLED"
        }
    }
}
```

---

### 2.4 `list-configuration-sets`

Lists all configuration sets in the account. **Paginated operation.**

**Synopsis:**
```bash
aws sesv2 list-configuration-sets \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (max 1000) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConfigurationSets": ["string"],
    "NextToken": "string"
}
```

---

### 2.5 `create-configuration-set-event-destination`

Creates an event destination for a configuration set. Events can be sent to CloudWatch, SNS, Kinesis Data Firehose, or EventBridge.

**Synopsis:**
```bash
aws sesv2 create-configuration-set-event-destination \
    --configuration-set-name <value> \
    --event-destination-name <value> \
    --event-destination <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-set-name` | **Yes** | string | -- | Configuration set name |
| `--event-destination-name` | **Yes** | string | -- | Name for the event destination |
| `--event-destination` | **Yes** | structure | -- | Event destination definition |

**Event Destination Structure:**
```json
{
    "Enabled": true|false,
    "MatchingEventTypes": ["SEND"|"REJECT"|"BOUNCE"|"COMPLAINT"|"DELIVERY"|"OPEN"|"CLICK"|"RENDERING_FAILURE"|"DELIVERY_DELAY"|"SUBSCRIPTION"],
    "KinesisFirehoseDestination": {
        "IamRoleArn": "string",
        "DeliveryStreamArn": "string"
    },
    "CloudWatchDestination": {
        "DimensionConfigurations": [
            {
                "DimensionName": "string",
                "DimensionValueSource": "MESSAGE_TAG|EMAIL_HEADER|LINK_TAG",
                "DefaultDimensionValue": "string"
            }
        ]
    },
    "SnsDestination": {
        "TopicArn": "string"
    },
    "EventBridgeDestination": {
        "EventBusArn": "string"
    },
    "PinpointDestination": {
        "ApplicationArn": "string"
    }
}
```

**Output Schema:**
```json
{}
```

---

### 2.6 `delete-configuration-set-event-destination`

Deletes an event destination from a configuration set.

**Synopsis:**
```bash
aws sesv2 delete-configuration-set-event-destination \
    --configuration-set-name <value> \
    --event-destination-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-set-name` | **Yes** | string | -- | Configuration set name |
| `--event-destination-name` | **Yes** | string | -- | Event destination name to delete |

**Output Schema:**
```json
{}
```

---

### 2.7 `get-configuration-set-event-destinations`

Retrieves all event destinations associated with a configuration set.

**Synopsis:**
```bash
aws sesv2 get-configuration-set-event-destinations \
    --configuration-set-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-set-name` | **Yes** | string | -- | Configuration set name |

**Output Schema:**
```json
{
    "EventDestinations": [
        {
            "Name": "string",
            "Enabled": true|false,
            "MatchingEventTypes": ["SEND"|"REJECT"|"BOUNCE"|"COMPLAINT"|"DELIVERY"|"OPEN"|"CLICK"|"RENDERING_FAILURE"|"DELIVERY_DELAY"|"SUBSCRIPTION"],
            "KinesisFirehoseDestination": {
                "IamRoleArn": "string",
                "DeliveryStreamArn": "string"
            },
            "CloudWatchDestination": {
                "DimensionConfigurations": []
            },
            "SnsDestination": {
                "TopicArn": "string"
            },
            "EventBridgeDestination": {
                "EventBusArn": "string"
            },
            "PinpointDestination": {
                "ApplicationArn": "string"
            }
        }
    ]
}
```

---

### 2.8 `update-configuration-set-event-destination`

Updates an event destination for a configuration set.

**Synopsis:**
```bash
aws sesv2 update-configuration-set-event-destination \
    --configuration-set-name <value> \
    --event-destination-name <value> \
    --event-destination <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-set-name` | **Yes** | string | -- | Configuration set name |
| `--event-destination-name` | **Yes** | string | -- | Event destination name to update |
| `--event-destination` | **Yes** | structure | -- | Updated event destination definition (same structure as create) |

**Output Schema:**
```json
{}
```
