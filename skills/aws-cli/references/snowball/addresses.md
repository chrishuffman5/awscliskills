# Addresses

### 3.1 `create-address`

Creates a shipping address for Snow Family device deliveries.

**Synopsis:**
```bash
aws snowball create-address \
    --address <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--address` | **Yes** | structure | -- | The address where the Snow device should be shipped |

**Address Structure:**
```json
{
    "Name": "string",
    "Company": "string",
    "Street1": "string",
    "Street2": "string",
    "Street3": "string",
    "City": "string",
    "StateOrProvince": "string",
    "Country": "string",
    "PostalCode": "string",
    "PhoneNumber": "string",
    "IsRestricted": true|false,
    "Type": "CUST_PICKUP|AWS_SHIP"
}
```

All address fields are strings with max length 1024 characters.

**Shorthand Syntax:**
```bash
aws snowball create-address \
  --address Name="John Doe",Company="Acme Corp",Street1="123 Main St",City="Seattle",StateOrProvince="WA",Country="US",PostalCode="98101",PhoneNumber="206-555-0100"
```

**Output Schema:**
```json
{
    "AddressId": "string"
}
```

---

### 3.2 `describe-address`

Returns information about a specific address.

**Synopsis:**
```bash
aws snowball describe-address \
    --address-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--address-id` | **Yes** | string | -- | Address ID (40 chars, pattern: `ADID...`) |

**Output Schema:**
```json
{
    "Address": {
        "AddressId": "string",
        "Name": "string",
        "Company": "string",
        "Street1": "string",
        "Street2": "string",
        "Street3": "string",
        "City": "string",
        "StateOrProvince": "string",
        "PrefectureOrDistrict": "string",
        "Landmark": "string",
        "Country": "string",
        "PostalCode": "string",
        "PhoneNumber": "string",
        "IsRestricted": "boolean",
        "Type": "CUST_PICKUP|AWS_SHIP"
    }
}
```

> **Note:** `PrefectureOrDistrict` and `Landmark` fields are deprecated and no longer used.

---

### 3.3 `describe-addresses`

Returns all addresses in the account. When calling from US regions, returns addresses from all US regions. **Paginated operation.**

**Synopsis:**
```bash
aws snowball describe-addresses \
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
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Addresses": [
        {
            "AddressId": "string",
            "Name": "string",
            "Company": "string",
            "Street1": "string",
            "Street2": "string",
            "Street3": "string",
            "City": "string",
            "StateOrProvince": "string",
            "PrefectureOrDistrict": "string",
            "Landmark": "string",
            "Country": "string",
            "PostalCode": "string",
            "PhoneNumber": "string",
            "IsRestricted": "boolean",
            "Type": "CUST_PICKUP|AWS_SHIP"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `list-pickup-locations`

Returns a list of available pickup locations for Snow devices.

**Synopsis:**
```bash
aws snowball list-pickup-locations \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Maximum locations per page (0-100) |
| `--next-token` | No | string | None | Pagination token from previous response |

**Output Schema:**
```json
{
    "Addresses": [
        {
            "AddressId": "string",
            "Name": "string",
            "Company": "string",
            "Street1": "string",
            "Street2": "string",
            "Street3": "string",
            "City": "string",
            "StateOrProvince": "string",
            "Country": "string",
            "PostalCode": "string",
            "PhoneNumber": "string",
            "IsRestricted": "boolean",
            "Type": "CUST_PICKUP|AWS_SHIP"
        }
    ],
    "NextToken": "string"
}
```
