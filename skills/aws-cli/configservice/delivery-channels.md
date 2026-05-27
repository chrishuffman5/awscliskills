# Delivery Channels

### 4.1 `put-delivery-channel`

Creates or updates a delivery channel. A delivery channel specifies how Config delivers configuration snapshots and configuration history to an S3 bucket and optionally sends notifications to an SNS topic.

**Synopsis:**
```bash
aws configservice put-delivery-channel \
    --delivery-channel <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-channel` | **Yes** | structure | -- | Delivery channel configuration |

**Delivery Channel Structure:**
```json
{
    "name": "string",
    "s3BucketName": "string",
    "s3KeyPrefix": "string",
    "s3KmsKeyArn": "string",
    "snsTopicARN": "string",
    "configSnapshotDeliveryProperties": {
        "deliveryFrequency": "One_Hour|Three_Hours|Six_Hours|Twelve_Hours|TwentyFour_Hours"
    }
}
```

**Output Schema:**
```json
{}
```

---

### 4.2 `delete-delivery-channel`

Deletes the delivery channel. Before you delete the delivery channel, you must stop the configuration recorder.

**Synopsis:**
```bash
aws configservice delete-delivery-channel \
    --delivery-channel-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-channel-name` | **Yes** | string | -- | Name of the delivery channel to delete |

**Output Schema:**
```json
{}
```

---

### 4.3 `describe-delivery-channels`

Returns details about the specified delivery channels.

**Synopsis:**
```bash
aws configservice describe-delivery-channels \
    [--delivery-channel-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-channel-names` | No | list(string) | None | Specific delivery channel names (currently only one per account) |

**Output Schema:**
```json
{
    "DeliveryChannels": [
        {
            "name": "string",
            "s3BucketName": "string",
            "s3KeyPrefix": "string",
            "s3KmsKeyArn": "string",
            "snsTopicARN": "string",
            "configSnapshotDeliveryProperties": {
                "deliveryFrequency": "One_Hour|Three_Hours|Six_Hours|Twelve_Hours|TwentyFour_Hours"
            }
        }
    ]
}
```

---

### 4.4 `describe-delivery-channel-status`

Returns the current status of the specified delivery channel.

**Synopsis:**
```bash
aws configservice describe-delivery-channel-status \
    [--delivery-channel-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-channel-names` | No | list(string) | None | Specific delivery channel names |

**Output Schema:**
```json
{
    "DeliveryChannelsStatus": [
        {
            "name": "string",
            "configSnapshotDeliveryInfo": {
                "lastStatus": "Success|Failure|Not_Applicable",
                "lastErrorCode": "string",
                "lastErrorMessage": "string",
                "lastAttemptTime": "timestamp",
                "lastSuccessfulTime": "timestamp",
                "nextDeliveryTime": "timestamp"
            },
            "configHistoryDeliveryInfo": {
                "lastStatus": "Success|Failure|Not_Applicable",
                "lastErrorCode": "string",
                "lastErrorMessage": "string",
                "lastAttemptTime": "timestamp",
                "lastSuccessfulTime": "timestamp",
                "nextDeliveryTime": "timestamp"
            },
            "configStreamDeliveryInfo": {
                "lastStatus": "Success|Failure|Not_Applicable",
                "lastErrorCode": "string",
                "lastErrorMessage": "string",
                "lastStatusChangeTime": "timestamp"
            }
        }
    ]
}
```

---

### 4.5 `deliver-config-snapshot`

Schedules delivery of a configuration snapshot to the S3 bucket in the delivery channel.

**Synopsis:**
```bash
aws configservice deliver-config-snapshot \
    --delivery-channel-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-channel-name` | **Yes** | string | -- | Name of the delivery channel |

**Output Schema:**
```json
{
    "configSnapshotId": "string"
}
```
