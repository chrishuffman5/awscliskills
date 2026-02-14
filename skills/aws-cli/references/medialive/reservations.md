# Reservations & Offerings

### 7.1 `purchase-offering`

Purchases a reserved capacity offering.

**Synopsis:**
```bash
aws medialive purchase-offering \
    --count <value> \
    --offering-id <value> \
    [--name <value>] \
    [--renewal-settings <value>] \
    [--request-id <value>] \
    [--start <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--count` | **Yes** | integer | -- | Number of resources to reserve |
| `--offering-id` | **Yes** | string | -- | Offering ID to purchase |
| `--name` | No | string | None | Reservation name |
| `--renewal-settings` | No | structure | None | Auto-renewal settings |
| `--request-id` | No | string | Auto | Idempotency token |
| `--start` | No | string | Now | Start time in ISO-8601 UTC |
| `--tags` | No | map | None | Key-value tag pairs |

**RenewalSettings:**
```json
{
    "AutomaticRenewal": "DISABLED|ENABLED|UNAVAILABLE",
    "RenewalCount": 1
}
```

**Output Schema:**
```json
{
    "Reservation": {
        "Arn": "string",
        "ReservationId": "string",
        "Name": "string",
        "Count": "integer",
        "CurrencyCode": "string",
        "Duration": "integer",
        "DurationUnits": "MONTHS",
        "End": "string",
        "Start": "string",
        "FixedPrice": "double",
        "UsagePrice": "double",
        "OfferingDescription": "string",
        "OfferingId": "string",
        "OfferingType": "NO_UPFRONT",
        "Region": "string",
        "RenewalSettings": {},
        "ResourceSpecification": {
            "ChannelClass": "string",
            "Codec": "string",
            "MaximumBitrate": "string",
            "MaximumFramerate": "string",
            "Resolution": "string",
            "ResourceType": "string",
            "SpecialFeature": "string",
            "VideoQuality": "string"
        },
        "State": "ACTIVE|EXPIRED|CANCELED|DELETED",
        "Tags": {}
    }
}
```

---

### 7.2 `describe-offering`

Describes an available offering.

**Synopsis:**
```bash
aws medialive describe-offering \
    --offering-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--offering-id` | **Yes** | string | -- | Offering ID |

**Output Schema:**
```json
{
    "Arn": "string",
    "CurrencyCode": "string",
    "Duration": "integer",
    "DurationUnits": "MONTHS",
    "FixedPrice": "double",
    "OfferingDescription": "string",
    "OfferingId": "string",
    "OfferingType": "string",
    "Region": "string",
    "ResourceSpecification": {},
    "UsagePrice": "double"
}
```

---

### 7.3 `list-offerings`

Lists available offerings. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-offerings \
    [--channel-class <value>] \
    [--channel-configuration <value>] \
    [--codec <value>] \
    [--duration <value>] \
    [--maximum-bitrate <value>] \
    [--maximum-framerate <value>] \
    [--resolution <value>] \
    [--resource-type <value>] \
    [--special-feature <value>] \
    [--video-quality <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-class` | No | string | None | Filter by channel class |
| `--codec` | No | string | None | Filter by codec |
| `--duration` | No | string | None | Filter by duration |
| `--maximum-bitrate` | No | string | None | Filter by max bitrate |
| `--maximum-framerate` | No | string | None | Filter by max framerate |
| `--resolution` | No | string | None | Filter by resolution |
| `--resource-type` | No | string | None | Filter by resource type |
| `--special-feature` | No | string | None | Filter by special feature |
| `--video-quality` | No | string | None | Filter by video quality |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Offerings": [
        {
            "Arn": "string",
            "CurrencyCode": "string",
            "Duration": "integer",
            "DurationUnits": "MONTHS",
            "FixedPrice": "double",
            "OfferingDescription": "string",
            "OfferingId": "string",
            "OfferingType": "string",
            "Region": "string",
            "ResourceSpecification": {},
            "UsagePrice": "double"
        }
    ]
}
```

---

### 7.4 `describe-reservation`

Describes a reservation.

**Synopsis:**
```bash
aws medialive describe-reservation \
    --reservation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reservation-id` | **Yes** | string | -- | Reservation ID |

**Output Schema:** Same as `purchase-offering` Reservation output.

---

### 7.5 `update-reservation`

Updates a reservation's name or renewal settings.

**Synopsis:**
```bash
aws medialive update-reservation \
    --reservation-id <value> \
    [--name <value>] \
    [--renewal-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reservation-id` | **Yes** | string | -- | Reservation ID |
| `--name` | No | string | None | Updated name |
| `--renewal-settings` | No | structure | None | Updated renewal settings |

**Output Schema:**
```json
{
    "Reservation": {
        "Arn": "string",
        "ReservationId": "string",
        "Name": "string",
        "State": "string",
        "RenewalSettings": {}
    }
}
```

---

### 7.6 `delete-reservation`

Deletes a reservation.

**Synopsis:**
```bash
aws medialive delete-reservation \
    --reservation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reservation-id` | **Yes** | string | -- | Reservation ID to delete |

**Output Schema:**
```json
{
    "Arn": "string",
    "ReservationId": "string",
    "Name": "string",
    "State": "DELETED"
}
```

---

### 7.7 `list-reservations`

Lists reservations. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-reservations \
    [--channel-class <value>] \
    [--codec <value>] \
    [--maximum-bitrate <value>] \
    [--maximum-framerate <value>] \
    [--resolution <value>] \
    [--resource-type <value>] \
    [--special-feature <value>] \
    [--video-quality <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-class` | No | string | None | Filter by channel class |
| `--codec` | No | string | None | Filter by codec |
| `--maximum-bitrate` | No | string | None | Filter by max bitrate |
| `--resolution` | No | string | None | Filter by resolution |
| `--resource-type` | No | string | None | Filter by resource type |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Reservations": [
        {
            "Arn": "string",
            "ReservationId": "string",
            "Name": "string",
            "Count": "integer",
            "State": "string",
            "Start": "string",
            "End": "string",
            "OfferingDescription": "string",
            "ResourceSpecification": {},
            "Tags": {}
        }
    ]
}
```
