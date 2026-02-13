# Route Calculators

### 5.1 `create-route-calculator`

Creates a route calculator resource (v1 API).

**Synopsis:**
```bash
aws location create-route-calculator \
    --calculator-name <value> \
    --data-source <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--calculator-name` | **Yes** | string | -- | Calculator name (1-100 chars) |
| `--data-source` | **Yes** | string | -- | Provider: `Esri`, `Grab`, or `Here` |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--tags` | No | map | None | Resource tags (max 50) |

**Output Schema:**
```json
{ "CalculatorName": "string", "CalculatorArn": "string", "CreateTime": "timestamp" }
```

---

### 5.2 `delete-route-calculator`

**Synopsis:** `aws location delete-route-calculator --calculator-name <value>`

**Output:** None.

---

### 5.3 `describe-route-calculator`

**Synopsis:** `aws location describe-route-calculator --calculator-name <value>`

**Output Schema:**
```json
{
    "CalculatorName": "string", "CalculatorArn": "string", "Description": "string",
    "DataSource": "string", "Tags": {}, "CreateTime": "timestamp", "UpdateTime": "timestamp"
}
```

---

### 5.4 `list-route-calculators`

**Paginated.** Synopsis: `aws location list-route-calculators [--starting-token <value>] [--page-size <value>] [--max-items <value>]`

**Output Schema:**
```json
{ "Entries": [{ "CalculatorName": "string", "Description": "string", "DataSource": "string", "CreateTime": "timestamp", "UpdateTime": "timestamp" }], "NextToken": "string" }
```

---

### 5.5 `update-route-calculator`

**Synopsis:** `aws location update-route-calculator --calculator-name <value> [--description <value>]`

**Output Schema:**
```json
{ "CalculatorName": "string", "CalculatorArn": "string", "UpdateTime": "timestamp" }
```

---

### 5.6 `calculate-route`

Calculates a route between two positions with optional waypoints (v1 API).

**Synopsis:**
```bash
aws location calculate-route \
    --calculator-name <value> \
    --departure-position <value> \
    --destination-position <value> \
    [--waypoint-positions <value>] \
    [--travel-mode <value>] \
    [--departure-time <value>] \
    [--depart-now | --no-depart-now] \
    [--distance-unit <value>] \
    [--include-leg-geometry | --no-include-leg-geometry] \
    [--car-mode-options <value>] \
    [--truck-mode-options <value>] \
    [--arrival-time <value>] \
    [--optimize-for <value>] \
    [--key <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--calculator-name` | **Yes** | string | -- | Route calculator name |
| `--departure-position` | **Yes** | list(double) | -- | Start `[longitude, latitude]` |
| `--destination-position` | **Yes** | list(double) | -- | End `[longitude, latitude]` |
| `--waypoint-positions` | No | list | None | Up to 23 intermediate positions |
| `--travel-mode` | No | string | `Car` | `Car`, `Truck`, `Walking`, `Bicycle`, `Motorcycle` |
| `--departure-time` | No | timestamp | None | ISO 8601 departure time |
| `--depart-now` | No | boolean | false | Use current time |
| `--distance-unit` | No | string | `Kilometers` | `Kilometers` or `Miles` |
| `--include-leg-geometry` | No | boolean | false | Include route geometry |
| `--car-mode-options` | No | structure | None | `{ "AvoidFerries": bool, "AvoidTolls": bool }` |
| `--truck-mode-options` | No | structure | None | Truck dimensions, weight, and avoidance options |
| `--optimize-for` | No | string | None | `FastestRoute` or `ShortestRoute` |
| `--key` | No | string | None | API key |

**Output Schema:**
```json
{
    "Legs": [
        {
            "StartPosition": ["double","double"],
            "EndPosition": ["double","double"],
            "Distance": "double",
            "DurationSeconds": "double",
            "Geometry": { "LineString": [["double","double"]] },
            "Steps": [{ "StartPosition": [], "EndPosition": [], "Distance": "double", "DurationSeconds": "double", "GeometryOffset": "integer" }]
        }
    ],
    "Summary": {
        "RouteBBox": ["double","double","double","double"],
        "DataSource": "string",
        "Distance": "double",
        "DurationSeconds": "double",
        "DistanceUnit": "string"
    }
}
```

---

### 5.7 `calculate-route-matrix`

Calculates a matrix of routes between multiple departure and destination positions.

**Synopsis:**
```bash
aws location calculate-route-matrix \
    --calculator-name <value> \
    --departure-positions <value> \
    --destination-positions <value> \
    [--travel-mode <value>] \
    [--departure-time <value>] \
    [--depart-now | --no-depart-now] \
    [--distance-unit <value>] \
    [--car-mode-options <value>] \
    [--truck-mode-options <value>] \
    [--key <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--calculator-name` | **Yes** | string | -- | Route calculator name |
| `--departure-positions` | **Yes** | list | -- | Departure positions (1-5) |
| `--destination-positions` | **Yes** | list | -- | Destination positions (1-5) |
| `--travel-mode` | No | string | `Car` | Travel mode |
| `--distance-unit` | No | string | `Kilometers` | Distance unit |

**Output Schema:**
```json
{
    "RouteMatrix": [
        [
            { "Distance": "double", "DurationSeconds": "double", "Error": { "Code": "string", "Message": "string" } }
        ]
    ],
    "Summary": {
        "DataSource": "string",
        "RouteCount": "integer",
        "ErrorCount": "integer",
        "DistanceUnit": "string"
    },
    "SnappedDeparturePositions": [["double","double"]],
    "SnappedDestinationPositions": [["double","double"]]
}
```
