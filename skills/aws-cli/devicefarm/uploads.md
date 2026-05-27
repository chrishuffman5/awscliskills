# Uploads

### 5.1 `create-upload`

Creates a new upload in a project. Returns a pre-signed URL for uploading the file.

**Synopsis:**
```bash
aws devicefarm create-upload \
    --project-arn <value> \
    --name <value> \
    --type <value> \
    [--content-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the project |
| `--name` | **Yes** | string | -- | Name of the upload (typically the file name) |
| `--type` | **Yes** | string | -- | Upload type: `ANDROID_APP`, `IOS_APP`, `WEB_APP`, `EXTERNAL_DATA`, `APPIUM_JAVA_JUNIT_TEST_PACKAGE`, `APPIUM_JAVA_TESTNG_TEST_PACKAGE`, `APPIUM_PYTHON_TEST_PACKAGE`, `APPIUM_NODE_TEST_PACKAGE`, `APPIUM_RUBY_TEST_PACKAGE`, `APPIUM_WEB_JAVA_JUNIT_TEST_PACKAGE`, `APPIUM_WEB_JAVA_TESTNG_TEST_PACKAGE`, `APPIUM_WEB_PYTHON_TEST_PACKAGE`, `APPIUM_WEB_NODE_TEST_PACKAGE`, `APPIUM_WEB_RUBY_TEST_PACKAGE`, `CALABASH_TEST_PACKAGE`, `INSTRUMENTATION_TEST_PACKAGE`, `UIAUTOMATION_TEST_PACKAGE`, `UIAUTOMATOR_TEST_PACKAGE`, `XCTEST_TEST_PACKAGE`, `XCTEST_UI_TEST_PACKAGE`, `APPIUM_JAVA_JUNIT_TEST_SPEC`, `APPIUM_JAVA_TESTNG_TEST_SPEC`, `APPIUM_PYTHON_TEST_SPEC`, `APPIUM_NODE_TEST_SPEC`, `APPIUM_RUBY_TEST_SPEC`, `APPIUM_WEB_JAVA_JUNIT_TEST_SPEC`, `APPIUM_WEB_JAVA_TESTNG_TEST_SPEC`, `APPIUM_WEB_PYTHON_TEST_SPEC`, `APPIUM_WEB_NODE_TEST_SPEC`, `APPIUM_WEB_RUBY_TEST_SPEC`, `INSTRUMENTATION_TEST_SPEC`, `XCTEST_UI_TEST_SPEC` |
| `--content-type` | No | string | `application/octet-stream` | Content type of the upload |

**Output Schema:**
```json
{
    "upload": {
        "arn": "string",
        "name": "string",
        "created": "timestamp",
        "type": "string",
        "status": "INITIALIZED|PROCESSING|SUCCEEDED|FAILED",
        "url": "string",
        "metadata": "string",
        "contentType": "string",
        "message": "string",
        "category": "CURATED|PRIVATE"
    }
}
```

---

### 5.2 `delete-upload`

Deletes an upload.

**Synopsis:**
```bash
aws devicefarm delete-upload \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the upload to delete |

**Output Schema:**
```json
{}
```

---

### 5.3 `get-upload`

Gets information about an upload.

**Synopsis:**
```bash
aws devicefarm get-upload \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the upload |

**Output Schema:**
```json
{
    "upload": {
        "arn": "string",
        "name": "string",
        "created": "timestamp",
        "type": "string",
        "status": "INITIALIZED|PROCESSING|SUCCEEDED|FAILED",
        "url": "string",
        "metadata": "string",
        "contentType": "string",
        "message": "string",
        "category": "CURATED|PRIVATE"
    }
}
```

---

### 5.4 `list-uploads`

Gets information about uploads in a project. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-uploads \
    --arn <value> \
    [--type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the project |
| `--type` | No | string | None | Filter by upload type |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "uploads": [
        {
            "arn": "string",
            "name": "string",
            "created": "timestamp",
            "type": "string",
            "status": "INITIALIZED|PROCESSING|SUCCEEDED|FAILED",
            "url": "string",
            "metadata": "string",
            "contentType": "string",
            "message": "string",
            "category": "CURATED|PRIVATE"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.5 `update-upload`

Updates an uploaded test spec.

**Synopsis:**
```bash
aws devicefarm update-upload \
    --arn <value> \
    [--name <value>] \
    [--content-type <value>] \
    [--edit-content | --no-edit-content] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the upload to update |
| `--name` | No | string | None | Updated name |
| `--content-type` | No | string | None | Updated content type |
| `--edit-content` | No | boolean | None | Set to true if updating the content of the upload |

**Output Schema:**
```json
{
    "upload": {
        "arn": "string",
        "name": "string",
        "created": "timestamp",
        "type": "string",
        "status": "INITIALIZED|PROCESSING|SUCCEEDED|FAILED",
        "url": "string",
        "metadata": "string",
        "contentType": "string",
        "message": "string",
        "category": "CURATED|PRIVATE"
    }
}
```

---

### 5.6 `install-to-remote-access-session`

Installs an application to a device in a remote access session.

**Synopsis:**
```bash
aws devicefarm install-to-remote-access-session \
    --remote-access-session-arn <value> \
    --app-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--remote-access-session-arn` | **Yes** | string | -- | ARN of the remote access session |
| `--app-arn` | **Yes** | string | -- | ARN of the app to install |

**Output Schema:**
```json
{
    "appUpload": {
        "arn": "string",
        "name": "string",
        "created": "timestamp",
        "type": "string",
        "status": "INITIALIZED|PROCESSING|SUCCEEDED|FAILED",
        "url": "string",
        "metadata": "string",
        "contentType": "string",
        "message": "string",
        "category": "CURATED|PRIVATE"
    }
}
```
