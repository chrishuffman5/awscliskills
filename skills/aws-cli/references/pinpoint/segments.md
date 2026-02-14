# Segments

### 4.1 `create-segment`

Creates a segment for an application. Segments can be dimensional (dynamic) or imported (static).

**Synopsis:**
```bash
aws pinpoint create-segment \
    --application-id <value> \
    --write-segment-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--write-segment-request` | **Yes** | structure | -- | Segment configuration (JSON recommended) |

**WriteSegmentRequest Key Fields:**
- `Name` (string): Segment name
- `Dimensions` (structure): Segment criteria including `Attributes`, `Behavior`, `Demographic`, `Location`, `Metrics`, `UserAttributes`
- `SegmentGroups` (structure): Group-based segment with `Groups` array and `Include` (`ALL|ANY|NONE`)

**Dimensions Structure:**
- `Behavior.Recency`: `Duration` (`HR_24|DAY_7|DAY_14|DAY_30`), `RecencyType` (`ACTIVE|INACTIVE`)
- `Demographic`: `AppVersion`, `Channel`, `DeviceType`, `Make`, `Model`, `Platform` (each with `DimensionType` and `Values`)
- `Location`: `Country` (DimensionType/Values), `GPSPoint` (Coordinates/RangeInKilometers)
- `Attributes`/`UserAttributes`: `AttributeType` (`INCLUSIVE|EXCLUSIVE|CONTAINS|BEFORE|AFTER|ON|BETWEEN`), `Values`
- `Metrics`: `ComparisonOperator` (`GREATER_THAN|LESS_THAN|GREATER_THAN_OR_EQUAL|LESS_THAN_OR_EQUAL|EQUAL`), `Value`

**Output Schema:**
```json
{
    "SegmentResponse": {
        "ApplicationId": "string",
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "SegmentType": "DIMENSIONAL|IMPORT",
        "Dimensions": {},
        "SegmentGroups": {},
        "CreationDate": "string",
        "LastModifiedDate": "string",
        "Version": "integer",
        "tags": {"string": "string"}
    }
}
```

---

### 4.2 `get-segment`

Gets information about a segment.

**Synopsis:**
```bash
aws pinpoint get-segment \
    --application-id <value> \
    --segment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--segment-id` | **Yes** | string | -- | Segment ID |

**Output Schema:** Same as `SegmentResponse` above.

---

### 4.3 `get-segments`

Lists segments for an application.

**Synopsis:**
```bash
aws pinpoint get-segments \
    --application-id <value> \
    [--page-size <value>] \
    [--token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--page-size` | No | string | None | Max items per page |
| `--token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "SegmentsResponse": {
        "Item": [{"SegmentResponse": "..."}],
        "NextToken": "string"
    }
}
```

---

### 4.4 `update-segment`

Updates a segment.

**Synopsis:**
```bash
aws pinpoint update-segment \
    --application-id <value> \
    --segment-id <value> \
    --write-segment-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--segment-id` | **Yes** | string | -- | Segment ID |
| `--write-segment-request` | **Yes** | structure | -- | Updated segment configuration |

**Output Schema:** Same as `SegmentResponse`.

---

### 4.5 `delete-segment`

Deletes a segment.

**Synopsis:**
```bash
aws pinpoint delete-segment \
    --application-id <value> \
    --segment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--segment-id` | **Yes** | string | -- | Segment ID |

**Output Schema:** Same as `SegmentResponse`.

---

### 4.6 `get-segment-version` / 4.7 `get-segment-versions`

Get a specific segment version or list all versions.

**Synopsis:**
```bash
aws pinpoint get-segment-version \
    --application-id <value> \
    --segment-id <value> \
    --version <value>

aws pinpoint get-segment-versions \
    --application-id <value> \
    --segment-id <value> \
    [--page-size <value>] \
    [--token <value>]
```

---

### 4.8 `get-segment-export-jobs` / 4.9 `get-segment-import-jobs`

List export or import jobs for a segment.

**Synopsis:**
```bash
aws pinpoint get-segment-export-jobs \
    --application-id <value> \
    --segment-id <value> \
    [--page-size <value>] \
    [--token <value>]

aws pinpoint get-segment-import-jobs \
    --application-id <value> \
    --segment-id <value> \
    [--page-size <value>] \
    [--token <value>]
```
