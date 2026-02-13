# Geo Routes

Commands in the `aws geo-routes` namespace (v2 Routes API).

### 9.1 `calculate-routes`

Calculates optimal routes between an origin and destination with optional waypoints.

**Synopsis:**
```bash
aws geo-routes calculate-routes \
    --origin <value> \
    --destination <value> \
    [--waypoints <value>] \
    [--travel-mode <value>] \
    [--departure-time <value>] \
    [--arrival-time <value>] \
    [--depart-now | --no-depart-now] \
    [--optimize-routing-for <value>] \
    [--avoid <value>] \
    [--allow <value>] \
    [--exclude <value>] \
    [--tolls <value>] \
    [--traffic <value>] \
    [--travel-mode-options <value>] \
    [--instructions-measurement-system <value>] \
    [--leg-additional-features <value>] \
    [--leg-geometry-format <value>] \
    [--span-additional-features <value>] \
    [--travel-step-type <value>] \
    [--max-alternatives <value>] \
    [--driver <value>] \
    [--languages <value>] \
    [--key <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--origin` | **Yes** | list(double) | -- | Start `[longitude, latitude]` |
| `--destination` | **Yes** | list(double) | -- | End `[longitude, latitude]` |
| `--waypoints` | No | list | None | Intermediate waypoints with Position, StopDuration, PassThrough |
| `--travel-mode` | No | string | `Car` | `Car`, `Pedestrian`, `Scooter`, `Truck` |
| `--departure-time` | No | string | None | ISO 8601 departure time |
| `--arrival-time` | No | string | None | ISO 8601 arrival time |
| `--depart-now` | No | boolean | false | Use current time |
| `--optimize-routing-for` | No | string | `FastestRoute` | `FastestRoute` or `ShortestRoute` |
| `--avoid` | No | structure | None | Avoid features (Ferries, TollRoads, Tunnels, etc.) |
| `--traffic` | No | structure | None | Traffic data usage |
| `--travel-mode-options` | No | structure | None | Mode-specific options (truck dimensions, etc.) |
| `--instructions-measurement-system` | No | string | `Metric` | `Metric` or `Imperial` |
| `--leg-additional-features` | No | list | None | `Elevation`, `Incidents`, `Tolls`, `TravelStepInstructions`, etc. |
| `--leg-geometry-format` | No | string | None | `FlexiblePolyline` or `Simple` |
| `--max-alternatives` | No | integer | None | Alternative routes (0-5) |
| `--driver` | No | structure | None | Driver work-rest schedule |
| `--key` | No | string | None | API key |

**Output Schema:**
```json
{
    "LegGeometryFormat": "string",
    "PricingBucket": "string",
    "Notices": [{ "Code": "string", "Impact": "High|Low" }],
    "Routes": [
        {
            "Legs": [
                {
                    "Geometry": { "LineString": [], "Polyline": "string" },
                    "Language": "string",
                    "VehicleLegDetails": {
                        "Arrival": { "Place": { "Name": "string", "Position": [] }, "Time": "string" },
                        "Departure": { "Place": {}, "Time": "string" },
                        "Summary": { "Overview": { "Distance": "long", "Duration": "long" } },
                        "TravelSteps": [{ "Distance": "long", "Duration": "long", "Instruction": "string", "Type": "string" }],
                        "Spans": [{ "Country": "string", "Distance": "long", "Duration": "long", "SpeedLimit": {} }],
                        "Tolls": [{ "Country": "string", "Rates": [{ "Amount": "double", "Currency": "string" }] }]
                    }
                }
            ],
            "MajorRoadLabels": [{ "RoadName": {}, "RouteNumber": {} }],
            "Summary": { "Distance": "long", "Duration": "long", "Tolls": {} }
        }
    ]
}
```

---

### 9.2 `calculate-route-matrix`

Calculates a matrix of routes between multiple origins and destinations.

**Synopsis:**
```bash
aws geo-routes calculate-route-matrix \
    --origins <value> \
    --destinations <value> \
    [--routing-boundary <value>] \
    [--travel-mode <value>] \
    [--departure-time <value>] \
    [--depart-now | --no-depart-now] \
    [--optimize-routing-for <value>] \
    [--avoid <value>] \
    [--exclude <value>] \
    [--traffic <value>] \
    [--travel-mode-options <value>] \
    [--key <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--origins` | **Yes** | list | -- | Origin positions with options |
| `--destinations` | **Yes** | list | -- | Destination positions with options |
| `--routing-boundary` | No | structure | None | Bounding geometry for routing |
| `--travel-mode` | No | string | `Car` | Travel mode |

**Output Schema:**
```json
{
    "PricingBucket": "string",
    "ErrorCount": "integer",
    "RouteMatrix": [
        [
            { "Distance": "long", "Duration": "long", "Error": "string" }
        ]
    ],
    "RoutingBoundary": {}
}
```

---

### 9.3 `calculate-isolines`

Calculates reachable areas (isolines) based on time or distance thresholds.

**Synopsis:**
```bash
aws geo-routes calculate-isolines \
    --thresholds <value> \
    [--origin <value>] \
    [--destination <value>] \
    [--travel-mode <value>] \
    [--departure-time <value>] \
    [--arrival-time <value>] \
    [--depart-now | --no-depart-now] \
    [--optimize-isoline-for <value>] \
    [--optimize-routing-for <value>] \
    [--avoid <value>] \
    [--traffic <value>] \
    [--travel-mode-options <value>] \
    [--isoline-geometry-format <value>] \
    [--isoline-granularity <value>] \
    [--key <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thresholds` | **Yes** | structure | -- | Distance (meters, max 300000) and/or Time (seconds, max 10800) thresholds (1-5 values each) |
| `--origin` | No | list(double) | None | Start position `[longitude, latitude]` |
| `--destination` | No | list(double) | None | Destination position |
| `--travel-mode` | No | string | `Car` | `Car`, `Pedestrian`, `Scooter`, `Truck` |
| `--optimize-isoline-for` | No | string | `BalancedCalculation` | `AccurateCalculation`, `BalancedCalculation`, `FastCalculation` |
| `--isoline-geometry-format` | No | string | `FlexiblePolyline` | `FlexiblePolyline` or `Simple` |

**Output Schema:**
```json
{
    "PricingBucket": "string",
    "ArrivalTime": "string",
    "DepartureTime": "string",
    "IsolineGeometryFormat": "string",
    "Isolines": [
        {
            "DistanceThreshold": "long",
            "TimeThreshold": "long",
            "Geometries": [{ "Polygon": [[["double","double"]]], "PolylinePolygon": ["string"] }],
            "Connections": [{ "FromPolygonIndex": "integer", "ToPolygonIndex": "integer", "Geometry": {} }]
        }
    ],
    "SnappedOrigin": ["double","double"],
    "SnappedDestination": ["double","double"]
}
```

---

### 9.4 `optimize-waypoints`

Optimizes the order of waypoints to minimize travel time or distance.

**Synopsis:**
```bash
aws geo-routes optimize-waypoints \
    --origin <value> \
    [--destination <value>] \
    [--waypoints <value>] \
    [--travel-mode <value>] \
    [--departure-time <value>] \
    [--optimize-sequencing-for <value>] \
    [--avoid <value>] \
    [--exclude <value>] \
    [--traffic <value>] \
    [--travel-mode-options <value>] \
    [--driver <value>] \
    [--clustering <value>] \
    [--key <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--origin` | **Yes** | list(double) | -- | Start `[longitude, latitude]` |
| `--destination` | No | list(double) | None | End position |
| `--waypoints` | No | list | None | Waypoints with Position, access hours, appointment time, service duration |
| `--travel-mode` | No | string | `Car` | Travel mode |
| `--optimize-sequencing-for` | No | string | `FastestRoute` | `FastestRoute` or `ShortestRoute` |
| `--driver` | No | structure | None | Driver rest schedule |
| `--clustering` | No | structure | None | Waypoint clustering config |

**Output Schema:**
```json
{
    "PricingBucket": "string",
    "Distance": "long",
    "Duration": "long",
    "OptimizedWaypoints": [
        { "Id": "string", "Position": [], "DepartureTime": "string", "ArrivalTime": "string" }
    ],
    "Connections": [
        { "From": "string", "To": "string", "Distance": "long", "TravelDuration": "long", "WaitDuration": "long", "RestDuration": "long" }
    ],
    "TimeBreakdown": { "TravelDuration": "long", "RestDuration": "long", "ServiceDuration": "long", "WaitDuration": "long" },
    "ImpedingWaypoints": [
        { "Id": "string", "Position": [], "FailedConstraints": [{ "Constraint": "string", "Reason": "string" }] }
    ]
}
```

---

### 9.5 `snap-to-roads`

Aligns GPS traces to the road network through map-matching.

**Synopsis:**
```bash
aws geo-routes snap-to-roads \
    --trace-points <value> \
    [--travel-mode <value>] \
    [--travel-mode-options <value>] \
    [--snap-radius <value>] \
    [--snapped-geometry-format <value>] \
    [--key <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trace-points` | **Yes** | list | -- | GPS trace points with Position, Speed, Heading, Timestamp |
| `--travel-mode` | No | string | `Car` | Travel mode |
| `--snap-radius` | No | long | None | Max snap distance in meters |
| `--snapped-geometry-format` | No | string | `FlexiblePolyline` | `FlexiblePolyline` or `Simple` |

**Output Schema:**
```json
{
    "PricingBucket": "string",
    "SnappedGeometry": { "LineString": [], "Polyline": "string" },
    "SnappedGeometryFormat": "string",
    "SnappedTracePoints": [
        { "Confidence": "double", "OriginalPosition": [], "SnappedPosition": [] }
    ],
    "Notices": [{ "Code": "string", "Title": "string", "TracePointIndexes": ["integer"] }]
}
```
