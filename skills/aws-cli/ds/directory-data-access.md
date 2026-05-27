# Directory Data Access

### 9.1 `enable-directory-data-access`

Enables programmatic access to directory data (users, groups, etc.) through the Directory Service Data API.

**Synopsis:**
```bash
aws ds enable-directory-data-access \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |

**Output Schema:**

No output on success (HTTP 200).

---

### 9.2 `disable-directory-data-access`

Disables programmatic access to directory data.

**Synopsis:**
```bash
aws ds disable-directory-data-access \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |

**Output Schema:**

No output on success (HTTP 200).

---

### 9.3 `describe-directory-data-access`

Describes the status of directory data access for a directory.

**Synopsis:**
```bash
aws ds describe-directory-data-access \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |

**Output Schema:**
```json
{
    "DirectoryDataAccessStatus": "Enabled|Disabled|Enabling|Disabling|EnableFailed|DisableFailed"
}
```
