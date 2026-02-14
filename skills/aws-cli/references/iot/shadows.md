# Shadows

Commands from the `aws iot-data` service for managing device shadows.

## 5.1 `get-thing-shadow`

Gets the device shadow for a thing.

**Synopsis:**
```bash
aws iot-data get-thing-shadow \
    --thing-name <value> \
    [--shadow-name <value>] \
    outfile <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name (1-128 chars) |
| `--shadow-name` | No | string | None | Named shadow name (1-64 chars). Omit for classic shadow |
| `outfile` | **Yes** | string | -- | Output filename for shadow payload |

**Output:** Shadow payload saved to outfile as JSON blob:
```json
{
    "state": {
        "desired": {},
        "reported": {},
        "delta": {}
    },
    "metadata": {},
    "version": "integer",
    "timestamp": "integer"
}
```

---

## 5.2 `update-thing-shadow`

Updates the device shadow for a thing.

**Synopsis:**
```bash
aws iot-data update-thing-shadow \
    --thing-name <value> \
    --payload <value> \
    [--shadow-name <value>] \
    outfile <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name (1-128 chars) |
| `--payload` | **Yes** | blob | -- | Shadow state JSON (desired/reported) |
| `--shadow-name` | No | string | None | Named shadow name (1-64 chars) |
| `outfile` | **Yes** | string | -- | Output filename for response payload |

**Payload format:**
```json
{
    "state": {
        "desired": {"key": "value"},
        "reported": {"key": "value"}
    }
}
```

**Output:** Response payload saved to outfile as JSON blob with updated state, metadata, version, and timestamp.

---

## 5.3 `delete-thing-shadow`

Deletes the device shadow for a thing.

**Synopsis:**
```bash
aws iot-data delete-thing-shadow \
    --thing-name <value> \
    [--shadow-name <value>] \
    outfile <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name (1-128 chars) |
| `--shadow-name` | No | string | None | Named shadow name (1-64 chars) |
| `outfile` | **Yes** | string | -- | Output filename for response payload |

**Output:** Response payload saved to outfile.

---

## 5.4 `list-named-shadows-for-thing`

Lists named shadows for a thing. **Paginated operation.**

**Synopsis:**
```bash
aws iot-data list-named-shadows-for-thing \
    --thing-name <value> \
    [--next-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name (1-128 chars) |
| `--next-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Max results per page |

**Output Schema:**
```json
{
    "results": ["string"],
    "nextToken": "string",
    "timestamp": "long"
}
```
