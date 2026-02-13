# AWS CLI v2 — Location Services Command Reference Index

> Based on AWS CLI v2 documentation.
> Sources:
> - https://docs.aws.amazon.com/cli/latest/reference/location/
> - https://docs.aws.amazon.com/cli/latest/reference/geo-maps/
> - https://docs.aws.amazon.com/cli/latest/reference/geo-places/
> - https://docs.aws.amazon.com/cli/latest/reference/geo-routes/

---

## Quick Reference

| Command | Namespace | Category | Description |
|---------|-----------|----------|-------------|
| `create-tracker` | location | Tracker | Create a new tracker resource |
| `delete-tracker` | location | Tracker | Delete a tracker |
| `describe-tracker` | location | Tracker | Get tracker details |
| `list-trackers` | location | Tracker | List all trackers |
| `update-tracker` | location | Tracker | Update tracker settings |
| `batch-update-device-position` | location | Tracker | Update positions for up to 10 devices |
| `batch-get-device-position` | location | Tracker | Get positions for multiple devices |
| `batch-delete-device-position-history` | location | Tracker | Delete position history for devices |
| `get-device-position` | location | Tracker | Get current device position |
| `get-device-position-history` | location | Tracker | Get device position history |
| `list-device-positions` | location | Tracker | List all device positions |
| `verify-device-position` | location | Tracker | Verify device position against geofences |
| `associate-tracker-consumer` | location | Tracker | Associate a geofence collection with a tracker |
| `disassociate-tracker-consumer` | location | Tracker | Disassociate a consumer from a tracker |
| `list-tracker-consumers` | location | Tracker | List consumers for a tracker |
| `create-geofence-collection` | location | Geofence | Create a geofence collection |
| `delete-geofence-collection` | location | Geofence | Delete a geofence collection |
| `describe-geofence-collection` | location | Geofence | Get geofence collection details |
| `list-geofence-collections` | location | Geofence | List all geofence collections |
| `update-geofence-collection` | location | Geofence | Update a geofence collection |
| `put-geofence` | location | Geofence | Add or update a geofence |
| `get-geofence` | location | Geofence | Get geofence details |
| `list-geofences` | location | Geofence | List geofences in a collection |
| `batch-put-geofence` | location | Geofence | Add multiple geofences |
| `batch-delete-geofence` | location | Geofence | Delete multiple geofences |
| `batch-evaluate-geofences` | location | Geofence | Evaluate device positions against geofences |
| `forecast-geofence-events` | location | Geofence | Forecast geofence entry/exit events |
| `create-map` | location | Map | Create a map resource |
| `delete-map` | location | Map | Delete a map |
| `describe-map` | location | Map | Get map details |
| `list-maps` | location | Map | List all maps |
| `update-map` | location | Map | Update map settings |
| `get-map-tile` | location | Map | Get a map tile |
| `get-map-glyphs` | location | Map | Get map glyphs (fonts) |
| `get-map-sprites` | location | Map | Get map sprites (icons) |
| `get-map-style-descriptor` | location | Map | Get map style descriptor |
| `create-place-index` | location | Place Index | Create a place index |
| `delete-place-index` | location | Place Index | Delete a place index |
| `describe-place-index` | location | Place Index | Get place index details |
| `list-place-indexes` | location | Place Index | List all place indexes |
| `update-place-index` | location | Place Index | Update a place index |
| `search-place-index-for-text` | location | Place Index | Search places by text |
| `search-place-index-for-position` | location | Place Index | Search places by position |
| `search-place-index-for-suggestions` | location | Place Index | Get place suggestions |
| `get-place` | location | Place Index | Get place details |
| `create-route-calculator` | location | Route Calculator | Create a route calculator |
| `delete-route-calculator` | location | Route Calculator | Delete a route calculator |
| `describe-route-calculator` | location | Route Calculator | Get route calculator details |
| `list-route-calculators` | location | Route Calculator | List all route calculators |
| `update-route-calculator` | location | Route Calculator | Update a route calculator |
| `calculate-route` | location | Route Calculator | Calculate a route |
| `calculate-route-matrix` | location | Route Calculator | Calculate a route matrix |
| `create-key` | location | Key | Create an API key |
| `delete-key` | location | Key | Delete an API key |
| `describe-key` | location | Key | Get API key details |
| `list-keys` | location | Key | List all API keys |
| `update-key` | location | Key | Update an API key |
| `tag-resource` | location | Tags | Add tags to a resource |
| `untag-resource` | location | Tags | Remove tags from a resource |
| `list-tags-for-resource` | location | Tags | List tags for a resource |
| `get-tile` | geo-maps | Geo Maps | Get a map tile (v2) |
| `get-glyphs` | geo-maps | Geo Maps | Get map glyphs (v2) |
| `get-sprites` | geo-maps | Geo Maps | Get map sprites (v2) |
| `get-style-descriptor` | geo-maps | Geo Maps | Get map style descriptor (v2) |
| `get-static-map` | geo-maps | Geo Maps | Generate a static map image (v2) |
| `geocode` | geo-places | Geo Places | Forward geocode an address (v2) |
| `reverse-geocode` | geo-places | Geo Places | Reverse geocode coordinates (v2) |
| `search-text` | geo-places | Geo Places | Search for places by text (v2) |
| `search-nearby` | geo-places | Geo Places | Search for nearby places (v2) |
| `get-place` | geo-places | Geo Places | Get place details (v2) |
| `autocomplete` | geo-places | Geo Places | Autocomplete place names (v2) |
| `suggest` | geo-places | Geo Places | Get place suggestions (v2) |
| `calculate-routes` | geo-routes | Geo Routes | Calculate optimal routes (v2) |
| `calculate-route-matrix` | geo-routes | Geo Routes | Calculate route matrix (v2) |
| `calculate-isolines` | geo-routes | Geo Routes | Calculate reachable areas (v2) |
| `optimize-waypoints` | geo-routes | Geo Routes | Optimize waypoint order (v2) |
| `snap-to-roads` | geo-routes | Geo Routes | Snap GPS traces to roads (v2) |

---

## Global Options

These options are available on ALL `aws location`, `aws geo-maps`, `aws geo-places`, and `aws geo-routes` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Position Filtering Modes (Trackers)
| Mode | Description |
|------|-------------|
| `TimeBased` | Max one position per 30 seconds per device |
| `DistanceBased` | Only stores if device moved >30m |
| `AccuracyBased` | Only stores if device moved more than measured accuracy |

### Geofence Geometry Types
| Type | Description |
|------|-------------|
| `Polygon` | Closed polygon with exterior and optional interior rings |
| `Circle` | Center point with radius in meters (max 100,000) |
| `MultiPolygon` | Multiple polygons |
| `Geobuf` | Compact binary geometry format |

### Travel Modes
| Mode | Namespace | Description |
|------|-----------|-------------|
| `Car` | location, geo-routes | Standard car routing |
| `Truck` | location, geo-routes | Truck routing with vehicle constraints |
| `Walking` | location | Pedestrian routing |
| `Bicycle` | location | Bicycle routing |
| `Motorcycle` | location | Motorcycle routing |
| `Pedestrian` | geo-routes | Pedestrian routing (v2) |
| `Scooter` | geo-routes | Scooter routing (v2) |

### Data Providers (v1 API)
| Provider | Services |
|----------|----------|
| `Esri` | Maps, Places, Routes |
| `Here` | Maps, Places, Routes |
| `Grab` | Maps, Places, Routes (Southeast Asia) |
