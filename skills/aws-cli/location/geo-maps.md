# Geo Maps

Commands in the `aws geo-maps` namespace (v2 Maps API).

### 7.1 `get-tile`

Retrieves a vector or raster map tile.

**Synopsis:**
```bash
aws geo-maps get-tile \
    --tileset <value> \
    --z <value> --x <value> --y <value> \
    [--additional-features <value>] \
    [--key <value>] \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tileset` | **Yes** | string | -- | Tile set: `raster.satellite`, `vector.basemap`, `vector.traffic`, `raster.dem` |
| `--z` | **Yes** | string | -- | Zoom level |
| `--x` | **Yes** | string | -- | X tile coordinate |
| `--y` | **Yes** | string | -- | Y tile coordinate |
| `--additional-features` | No | list | None | Features: `ContourLines`, `Hillshade`, `Logistics`, `Transit` |
| `--key` | No | string | None | API key |
| `<outfile>` | **Yes** | string | -- | Output file path |

**Output:** Binary tile data. Response metadata: `ContentType`, `CacheControl`, `ETag`, `PricingBucket`.

---

### 7.2 `get-glyphs`

Retrieves glyph (font) data for map rendering.

**Synopsis:**
```bash
aws geo-maps get-glyphs \
    --font-stack <value> \
    --font-unicode-range <value> \
    [--key <value>] \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--font-stack` | **Yes** | string | -- | Font name (e.g., `Amazon Ember Regular`) |
| `--font-unicode-range` | **Yes** | string | -- | Unicode range (e.g., `0-255`) |
| `--key` | No | string | None | API key |
| `<outfile>` | **Yes** | string | -- | Output file path |

**Output:** Binary glyph data saved to outfile.

---

### 7.3 `get-sprites`

Retrieves sprite (icon) data for map rendering.

**Synopsis:**
```bash
aws geo-maps get-sprites \
    --file-name <value> \
    --style <value> \
    --color-scheme <value> \
    --variant <value> \
    [--key <value>] \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--file-name` | **Yes** | string | -- | Sprite file: `sprites` or `sprites@2x` (+ `.json` or `.png`) |
| `--style` | **Yes** | string | -- | Map style: `Standard` or `Satellite` |
| `--color-scheme` | **Yes** | string | -- | `Light` or `Dark` |
| `--variant` | **Yes** | string | -- | Sprite variant: `Default` |
| `--key` | No | string | None | API key |
| `<outfile>` | **Yes** | string | -- | Output file path |

**Output:** Sprite image or JSON saved to outfile.

---

### 7.4 `get-style-descriptor`

Retrieves the map style descriptor JSON.

**Synopsis:**
```bash
aws geo-maps get-style-descriptor \
    --style <value> \
    [--color-scheme <value>] \
    [--political-view <value>] \
    [--key <value>] \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--style` | **Yes** | string | -- | Map style: `Standard` or `Satellite` |
| `--color-scheme` | No | string | `Light` | `Light` or `Dark` |
| `--political-view` | No | string | None | Country code for political boundaries |
| `--key` | No | string | None | API key |
| `<outfile>` | **Yes** | string | -- | Output file path |

**Output:** JSON style descriptor saved to outfile.

---

### 7.5 `get-static-map`

Generates a static map image (JPEG).

**Synopsis:**
```bash
aws geo-maps get-static-map \
    --height <value> \
    --width <value> \
    --file-name <value> \
    [--center <value>] \
    [--zoom <value>] \
    [--radius <value>] \
    [--bounding-box <value>] \
    [--bounded-positions <value>] \
    [--style <value>] \
    [--color-scheme <value>] \
    [--compact-overlay <value>] \
    [--geo-json-overlay <value>] \
    [--label-size <value>] \
    [--language <value>] \
    [--padding <value>] \
    [--political-view <value>] \
    [--scale-bar-unit <value>] \
    [--crop-labels | --no-crop-labels] \
    [--key <value>] \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--height` | **Yes** | integer | -- | Image height (64-1400 pixels) |
| `--width` | **Yes** | integer | -- | Image width (64-1400 pixels) |
| `--file-name` | **Yes** | string | -- | `map` or `map@2x` (retina) |
| `--center` | No | string | None | Center `latitude,longitude` |
| `--zoom` | No | float | None | Zoom level (0-20) |
| `--radius` | No | long | None | Radius in meters (alternative to zoom) |
| `--bounding-box` | No | string | None | `swLng,swLat,neLng,neLat` |
| `--bounded-positions` | No | string | None | Coordinate pairs to encompass |
| `--style` | No | string | None | `Standard` or `Satellite` |
| `--color-scheme` | No | string | `Light` | `Light` or `Dark` |
| `--compact-overlay` | No | string | None | Overlay geometries (max 5000 chars) |
| `--geo-json-overlay` | No | string | None | GeoJSON FeatureCollection (max 4200 chars) |
| `--language` | No | string | None | BCP 47 language code |
| `--padding` | No | integer | None | Padding around overlays (0-350 px) |
| `--scale-bar-unit` | No | string | None | `Kilometers`, `Miles`, `KilometersMiles`, `MilesKilometers` |
| `--key` | No | string | None | API key |
| `<outfile>` | **Yes** | string | -- | Output file path |

**Output:** JPEG image saved to outfile. Response metadata: `ContentType`, `CacheControl`, `ETag`, `PricingBucket`.
