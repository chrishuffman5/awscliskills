# Place Indexes

### 4.1 `create-place-index`

Creates a place index resource for geocoding (v1 API).

**Synopsis:**
```bash
aws location create-place-index \
    --index-name <value> \
    --data-source <value> \
    [--description <value>] \
    [--data-source-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-name` | **Yes** | string | -- | Place index name (1-100 chars) |
| `--data-source` | **Yes** | string | -- | Provider: `Esri`, `Grab`, or `Here` |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--data-source-configuration` | No | structure | None | `{ "IntendedUse": "SingleUse|Storage" }` |
| `--tags` | No | map | None | Resource tags (max 50) |

**Output Schema:**
```json
{ "IndexName": "string", "IndexArn": "string", "CreateTime": "timestamp" }
```

---

### 4.2 `delete-place-index`

**Synopsis:** `aws location delete-place-index --index-name <value>`

**Output:** None.

---

### 4.3 `describe-place-index`

**Synopsis:** `aws location describe-place-index --index-name <value>`

**Output Schema:**
```json
{
    "IndexName": "string", "IndexArn": "string", "Description": "string",
    "DataSource": "string", "DataSourceConfiguration": { "IntendedUse": "string" },
    "Tags": {}, "CreateTime": "timestamp", "UpdateTime": "timestamp"
}
```

---

### 4.4 `list-place-indexes`

**Paginated.** Synopsis: `aws location list-place-indexes [--starting-token <value>] [--page-size <value>] [--max-items <value>]`

**Output Schema:**
```json
{ "Entries": [{ "IndexName": "string", "Description": "string", "DataSource": "string", "CreateTime": "timestamp", "UpdateTime": "timestamp" }], "NextToken": "string" }
```

---

### 4.5 `update-place-index`

**Synopsis:** `aws location update-place-index --index-name <value> [--description <value>] [--data-source-configuration <value>]`

**Output Schema:**
```json
{ "IndexName": "string", "IndexArn": "string", "UpdateTime": "timestamp" }
```

---

### 4.6 `search-place-index-for-text`

Geocodes free-form text into one or more place results.

**Synopsis:**
```bash
aws location search-place-index-for-text \
    --index-name <value> \
    --text <value> \
    [--bias-position <value>] \
    [--filter-b-box <value>] \
    [--filter-countries <value>] \
    [--filter-categories <value>] \
    [--max-results <value>] \
    [--language <value>] \
    [--key <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-name` | **Yes** | string | -- | Place index name |
| `--text` | **Yes** | string | -- | Search text (1-200 chars) |
| `--bias-position` | No | list(double) | None | Bias by `[longitude, latitude]` |
| `--filter-b-box` | No | list(double) | None | Bounding box `[swLng, swLat, neLng, neLat]` |
| `--filter-countries` | No | list(string) | None | Country codes (ISO 3166) |
| `--max-results` | No | integer | None | Max results (1-50) |
| `--language` | No | string | None | BCP 47 language code |

**Output Schema:**
```json
{
    "Summary": { "Text": "string", "BiasPosition": [], "FilterBBox": [], "DataSource": "string", "MaxResults": "integer" },
    "Results": [{ "Place": { "Label": "string", "Geometry": { "Point": ["double","double"] }, "Country": "string", "Region": "string", "Municipality": "string", "PostalCode": "string", "Street": "string", "AddressNumber": "string" }, "Distance": "double", "Relevance": "double", "PlaceId": "string" }]
}
```

---

### 4.7 `search-place-index-for-position`

Reverse geocodes coordinates to places.

**Synopsis:**
```bash
aws location search-place-index-for-position \
    --index-name <value> \
    --position <value> \
    [--max-results <value>] \
    [--language <value>] \
    [--key <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-name` | **Yes** | string | -- | Place index name |
| `--position` | **Yes** | list(double) | -- | `[longitude, latitude]` |
| `--max-results` | No | integer | None | Max results (1-50) |

**Output Schema:**
```json
{
    "Summary": { "Position": ["double","double"], "DataSource": "string", "MaxResults": "integer" },
    "Results": [{ "Place": { "Label": "string", "Geometry": { "Point": [] }, "Country": "string", "Region": "string", "Municipality": "string" }, "Distance": "double", "PlaceId": "string" }]
}
```

---

### 4.8 `search-place-index-for-suggestions`

Returns place suggestions for partial text.

**Synopsis:**
```bash
aws location search-place-index-for-suggestions \
    --index-name <value> \
    --text <value> \
    [--bias-position <value>] \
    [--filter-b-box <value>] \
    [--filter-countries <value>] \
    [--filter-categories <value>] \
    [--max-results <value>] \
    [--language <value>] \
    [--key <value>]
```

**Output Schema:**
```json
{
    "Summary": { "Text": "string", "DataSource": "string" },
    "Results": [{ "Text": "string", "PlaceId": "string", "Categories": ["string"], "SupplementalCategories": ["string"] }]
}
```

---

### 4.9 `get-place`

Retrieves details for a specific place by ID.

**Synopsis:**
```bash
aws location get-place --index-name <value> --place-id <value> [--language <value>] [--key <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--index-name` | **Yes** | string | -- | Place index name |
| `--place-id` | **Yes** | string | -- | Place identifier |
| `--language` | No | string | None | BCP 47 language code |

**Output Schema:**
```json
{
    "Place": {
        "Label": "string", "Geometry": { "Point": ["double","double"] },
        "Country": "string", "Region": "string", "SubRegion": "string",
        "Municipality": "string", "Neighborhood": "string", "PostalCode": "string",
        "Street": "string", "AddressNumber": "string", "Categories": ["string"],
        "TimeZone": { "Name": "string", "Offset": "string" }
    }
}
```
