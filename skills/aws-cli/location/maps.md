# Maps

### 3.1 `create-map`

Creates a map resource (v1 API).

**Synopsis:**
```bash
aws location create-map \
    --map-name <value> \
    --configuration <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--map-name` | **Yes** | string | -- | Map name (1-100 chars) |
| `--configuration` | **Yes** | structure | -- | Map configuration with Style |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--tags` | No | map | None | Resource tags (max 50) |

**Configuration:** `{ "Style": "string", "PoliticalView": "string", "CustomLayers": ["string"] }`

Styles: `VectorEsriStreets`, `VectorEsriTopographic`, `VectorHereExplore`, `RasterEsriImagery`, etc.

**Output Schema:**
```json
{ "MapName": "string", "MapArn": "string", "CreateTime": "timestamp" }
```

---

### 3.2 `delete-map`

**Synopsis:** `aws location delete-map --map-name <value>`

**Output:** None.

---

### 3.3 `describe-map`

**Synopsis:** `aws location describe-map --map-name <value>`

**Output Schema:**
```json
{
    "MapName": "string", "MapArn": "string", "Description": "string",
    "Configuration": { "Style": "string", "PoliticalView": "string", "CustomLayers": [] },
    "Tags": {}, "CreateTime": "timestamp", "UpdateTime": "timestamp"
}
```

---

### 3.4 `list-maps`

**Paginated.** Synopsis: `aws location list-maps [--starting-token <value>] [--page-size <value>] [--max-items <value>]`

**Output Schema:**
```json
{ "Entries": [{ "MapName": "string", "Description": "string", "DataSource": "string", "CreateTime": "timestamp", "UpdateTime": "timestamp" }], "NextToken": "string" }
```

---

### 3.5 `update-map`

**Synopsis:** `aws location update-map --map-name <value> [--description <value>] [--configuration <value>]`

**Output Schema:**
```json
{ "MapName": "string", "MapArn": "string", "UpdateTime": "timestamp" }
```

---

### 3.6 `get-map-tile`

Retrieves a map tile for rendering.

**Synopsis:**
```bash
aws location get-map-tile \
    --map-name <value> \
    --z <value> --x <value> --y <value> \
    [--key <value>] \
    <outfile>
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--map-name` | **Yes** | string | -- | Map resource name |
| `--z` | **Yes** | string | -- | Zoom level |
| `--x` | **Yes** | string | -- | X tile coordinate |
| `--y` | **Yes** | string | -- | Y tile coordinate |
| `--key` | No | string | None | API key |
| `<outfile>` | **Yes** | string | -- | Output file path |

**Output:** Binary tile data saved to outfile. Response includes `Blob`, `ContentType`, `CacheControl`.

---

### 3.7 `get-map-glyphs`

Retrieves map glyph (font) data.

**Synopsis:** `aws location get-map-glyphs --map-name <value> --font-stack <value> --font-unicode-range <value> [--key <value>] <outfile>`

---

### 3.8 `get-map-sprites`

Retrieves map sprite (icon) data.

**Synopsis:** `aws location get-map-sprites --map-name <value> --file-name <value> [--key <value>] <outfile>`

---

### 3.9 `get-map-style-descriptor`

Retrieves the map style descriptor JSON.

**Synopsis:** `aws location get-map-style-descriptor --map-name <value> [--key <value>] <outfile>`

**Output:** JSON style descriptor saved to outfile.
