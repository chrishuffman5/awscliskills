# Versions

### 6.1 `publish-version`

Creates an immutable version from the current code and configuration of `$LATEST`.

**Synopsis:**
```bash
aws lambda publish-version \
    --function-name <value> \
    [--code-sha256 <value>] \
    [--description <value>] \
    [--revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--code-sha256` | No | string | -- | Only publish if code SHA-256 matches (prevents stale publish) |
| `--description` | No | string | -- | Version description (0-256 chars) |
| `--revision-id` | No | string | -- | Only publish if revision ID matches |

**Output Schema:** Same as `create-function` output (FunctionConfiguration with a numeric `Version`).

---

### 6.2 `list-versions-by-function`

Lists all versions of a function. **Paginated operation.**

**Synopsis:**
```bash
aws lambda list-versions-by-function \
    --function-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-170 chars) |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Versions": [
        { "...FunctionConfiguration..." }
    ],
    "NextMarker": "string"
}
```

---
