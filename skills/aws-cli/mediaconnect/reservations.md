# Reservations

### 10.1 `list-offerings`

Lists available reservation offerings. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconnect list-offerings \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Offerings": [
        {
            "CurrencyCode": "string",
            "Duration": "integer",
            "DurationUnits": "MONTHS",
            "OfferingArn": "string",
            "OfferingDescription": "string",
            "PricePerUnit": "string",
            "PriceUnits": "HOURLY",
            "ResourceSpecification": {
                "ReservedBitrate": "integer",
                "ResourceType": "Mbps_Outbound_Bandwidth"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 10.2 `describe-offering`

Describes a reservation offering.

**Synopsis:**
```bash
aws mediaconnect describe-offering \
    --offering-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--offering-arn` | **Yes** | string | -- | ARN of the offering |

**Output Schema:**
```json
{
    "Offering": {
        "CurrencyCode": "string",
        "Duration": "integer",
        "DurationUnits": "MONTHS",
        "OfferingArn": "string",
        "OfferingDescription": "string",
        "PricePerUnit": "string",
        "PriceUnits": "HOURLY",
        "ResourceSpecification": {
            "ReservedBitrate": "integer",
            "ResourceType": "Mbps_Outbound_Bandwidth"
        }
    }
}
```

---

### 10.3 `purchase-offering`

Purchases a reservation for bandwidth.

**Synopsis:**
```bash
aws mediaconnect purchase-offering \
    --offering-arn <value> \
    --reservation-name <value> \
    --start <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--offering-arn` | **Yes** | string | -- | ARN of the offering to purchase |
| `--reservation-name` | **Yes** | string | -- | Name for the reservation |
| `--start` | **Yes** | string | -- | Start date/time in UTC (format: `YYYY-MM-DDTHH:mm:SSZ`) |

**Output Schema:**
```json
{
    "Reservation": {
        "CurrencyCode": "string",
        "Duration": "integer",
        "DurationUnits": "MONTHS",
        "End": "string",
        "OfferingArn": "string",
        "OfferingDescription": "string",
        "PricePerUnit": "string",
        "PriceUnits": "HOURLY",
        "ReservationArn": "string",
        "ReservationName": "string",
        "ReservationState": "ACTIVE|EXPIRED|PROCESSING|CANCELED",
        "ResourceSpecification": {
            "ReservedBitrate": "integer",
            "ResourceType": "Mbps_Outbound_Bandwidth"
        },
        "Start": "string"
    }
}
```

---

### 10.4 `list-reservations`

Lists all reservations. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconnect list-reservations \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Reservations": [
        {
            "CurrencyCode": "string",
            "Duration": "integer",
            "DurationUnits": "MONTHS",
            "End": "string",
            "OfferingArn": "string",
            "OfferingDescription": "string",
            "PricePerUnit": "string",
            "PriceUnits": "HOURLY",
            "ReservationArn": "string",
            "ReservationName": "string",
            "ReservationState": "ACTIVE|EXPIRED|PROCESSING|CANCELED",
            "ResourceSpecification": {},
            "Start": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.5 `describe-reservation`

Describes a reservation.

**Synopsis:**
```bash
aws mediaconnect describe-reservation \
    --reservation-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reservation-arn` | **Yes** | string | -- | ARN of the reservation |

**Output Schema:** Same as individual reservation object in `list-reservations`.
