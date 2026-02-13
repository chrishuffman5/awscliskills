# Geo Places

Commands in the `aws geo-places` namespace (v2 Places API).

### 8.1 `geocode`

Forward geocodes an address or place name to coordinates.

**Synopsis:**
```bash
aws geo-places geocode \
    [--query-text <value>] \
    [--query-components <value>] \
    [--max-results <value>] \
    [--bias-position <value>] \
    [--filter <value>] \
    [--additional-features <value>] \
    [--language <value>] \
    [--political-view <value>] \
    [--intended-use <value>] \
    [--key <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-text` | No | string | None | Free-form text (1-200 chars). One of `query-text` or `query-components` required |
| `--query-components` | No | structure | None | Structured query (Country, Region, Locality, Street, AddressNumber, PostalCode) |
| `--max-results` | No | integer | 20 | Max results (1-100) |
| `--bias-position` | No | list(double) | None | Bias by `[longitude, latitude]` |
| `--filter` | No | structure | None | Filter by IncludeCountries, IncludePlaceTypes |
| `--additional-features` | No | list | None | `TimeZone`, `Access`, `SecondaryAddresses`, `Intersections` |
| `--language` | No | string | None | BCP 47 language code |
| `--political-view` | No | string | None | Country code for political view |
| `--intended-use` | No | string | `SingleUse` | `SingleUse` or `Storage` |
| `--key` | No | string | None | API key |

**Output Schema:**
```json
{
    "PricingBucket": "string",
    "ResultItems": [
        {
            "PlaceId": "string",
            "PlaceType": "string",
            "Title": "string",
            "Address": { "Label": "string", "Country": {}, "Region": {}, "Locality": "string", "Street": "string", "AddressNumber": "string", "PostalCode": "string" },
            "Position": ["double", "double"],
            "Distance": "long",
            "MapView": ["double","double","double","double"],
            "Categories": [{ "Id": "string", "Name": "string" }],
            "TimeZone": { "Name": "string", "Offset": "string" },
            "MatchScores": { "Overall": "double" }
        }
    ]
}
```

---

### 8.2 `reverse-geocode`

Reverse geocodes coordinates to addresses.

**Synopsis:**
```bash
aws geo-places reverse-geocode \
    --query-position <value> \
    [--query-radius <value>] \
    [--max-results <value>] \
    [--filter <value>] \
    [--additional-features <value>] \
    [--language <value>] \
    [--political-view <value>] \
    [--intended-use <value>] \
    [--heading <value>] \
    [--key <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-position` | **Yes** | list(double) | -- | `[longitude, latitude]` |
| `--query-radius` | No | long | None | Radius in meters (1-21,000,000) |
| `--max-results` | No | integer | 1 | Max results (1-100) |
| `--filter` | No | structure | None | IncludePlaceTypes filter |
| `--additional-features` | No | list | None | `TimeZone`, `Access`, `Intersections` |
| `--language` | No | string | None | BCP 47 language code |
| `--heading` | No | double | None | Navigation heading (0-360) |

**Output Schema:**
```json
{
    "PricingBucket": "string",
    "ResultItems": [
        {
            "PlaceId": "string", "PlaceType": "string", "Title": "string",
            "Address": { "Label": "string", "Country": {}, "Region": {}, "Locality": "string" },
            "Position": ["double","double"], "Distance": "long", "MapView": []
        }
    ]
}
```

---

### 8.3 `search-text`

Searches for places by free-form text or QueryId from suggest/autocomplete.

**Synopsis:**
```bash
aws geo-places search-text \
    [--query-text <value>] \
    [--query-id <value>] \
    [--max-results <value>] \
    [--bias-position <value>] \
    [--filter <value>] \
    [--additional-features <value>] \
    [--language <value>] \
    [--political-view <value>] \
    [--intended-use <value>] \
    [--next-token <value>] \
    [--key <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-text` | No | string | None | Search text (1-200 chars). One of `query-text` or `query-id` required |
| `--query-id` | No | string | None | QueryId from suggest API (1-500 chars) |
| `--max-results` | No | integer | 20 | Max results (1-100) |
| `--bias-position` | No | list(double) | None | Bias position |
| `--filter` | No | structure | None | BoundingBox, Circle, IncludeCountries |
| `--additional-features` | No | list | None | `TimeZone`, `Phonemes`, `Access`, `Contact` |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "PricingBucket": "string",
    "ResultItems": [
        {
            "PlaceId": "string", "PlaceType": "string", "Title": "string",
            "Address": {}, "Position": [], "Distance": "long",
            "Categories": [], "FoodTypes": [], "BusinessChains": [],
            "Contacts": { "Phones": [], "Websites": [] },
            "OpeningHours": [], "AccessPoints": [], "TimeZone": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 8.4 `search-nearby`

Searches for places near a specific location.

**Synopsis:**
```bash
aws geo-places search-nearby \
    --query-position <value> \
    [--query-radius <value>] \
    [--max-results <value>] \
    [--filter <value>] \
    [--additional-features <value>] \
    [--language <value>] \
    [--political-view <value>] \
    [--intended-use <value>] \
    [--next-token <value>] \
    [--key <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-position` | **Yes** | list(double) | -- | `[longitude, latitude]` |
| `--query-radius` | No | long | None | Search radius in meters |
| `--max-results` | No | integer | 20 | Max results (1-100) |
| `--filter` | No | structure | None | IncludeCategories, ExcludeCategories, IncludeBusinessChains, etc. |

**Output Schema:**
```json
{
    "PricingBucket": "string",
    "ResultItems": [
        { "PlaceId": "string", "PlaceType": "string", "Title": "string", "Address": {}, "Position": [], "Distance": "long", "Categories": [] }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `get-place`

Retrieves detailed place information by PlaceId.

**Synopsis:**
```bash
aws geo-places get-place \
    --place-id <value> \
    [--additional-features <value>] \
    [--language <value>] \
    [--political-view <value>] \
    [--intended-use <value>] \
    [--key <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--place-id` | **Yes** | string | -- | Place identifier |
| `--additional-features` | No | list | None | `TimeZone`, `Phonemes`, `Access`, `Contact` |

**Output Schema:**
```json
{
    "PricingBucket": "string", "PlaceId": "string", "PlaceType": "string",
    "Title": "string", "Address": {}, "Position": [], "MapView": [],
    "Categories": [], "FoodTypes": [], "BusinessChains": [],
    "Contacts": {}, "OpeningHours": [], "AccessPoints": [], "TimeZone": {}
}
```

---

### 8.6 `autocomplete`

Provides autocomplete suggestions for partial place names.

**Synopsis:**
```bash
aws geo-places autocomplete \
    --query-text <value> \
    [--max-results <value>] \
    [--bias-position <value>] \
    [--filter <value>] \
    [--language <value>] \
    [--political-view <value>] \
    [--intended-use <value>] \
    [--key <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-text` | **Yes** | string | -- | Partial text (1-200 chars) |
| `--max-results` | No | integer | None | Max results |
| `--bias-position` | No | list(double) | None | Bias position |

**Output Schema:**
```json
{
    "PricingBucket": "string",
    "ResultItems": [{ "PlaceId": "string", "PlaceType": "string", "Title": "string", "Address": {}, "Distance": "long", "Highlights": {} }]
}
```

---

### 8.7 `suggest`

Returns place suggestions based on partial input.

**Synopsis:**
```bash
aws geo-places suggest \
    --query-text <value> \
    [--max-results <value>] \
    [--max-query-refinements <value>] \
    [--bias-position <value>] \
    [--filter <value>] \
    [--additional-features <value>] \
    [--language <value>] \
    [--political-view <value>] \
    [--intended-use <value>] \
    [--key <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-text` | **Yes** | string | -- | Partial text (1-200 chars) |
| `--max-results` | No | integer | None | Max results |
| `--max-query-refinements` | No | integer | None | Max query refinement suggestions |

**Output Schema:**
```json
{
    "PricingBucket": "string",
    "ResultItems": [
        { "Title": "string", "SuggestResultItemType": "Place|Query", "Place": { "PlaceId": "string", "PlaceType": "string", "Address": {}, "Position": [], "Distance": "long", "Categories": [] }, "Query": { "QueryId": "string", "QueryType": "string" }, "Highlights": {} }
    ]
}
```
