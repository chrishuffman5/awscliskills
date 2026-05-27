# App Components

### 2.1 `create-app-version-app-component`

Adds an AppComponent to the draft version of a Resilience Hub application.

**Synopsis:**
```bash
aws resiliencehub create-app-version-app-component \
    --app-arn <value> \
    --name <value> \
    --type <value> \
    [--id <value>] \
    [--additional-info <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--name` | **Yes** | string | -- | Component name (1-255 chars) |
| `--type` | **Yes** | string | -- | Component type (e.g., `AWS::EC2::Instance`, `AWS::RDS::DBInstance`, `AWS::ECS::Service`) |
| `--id` | No | string | None | Component identifier (1-255 chars) |
| `--additional-info` | No | map | None | Additional info key-value map |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "appComponent": {
        "name": "string",
        "type": "string",
        "id": "string",
        "additionalInfo": {"string": ["string"]}
    }
}
```

---

### 2.2 `delete-app-version-app-component`

Deletes an AppComponent from the draft version.

**Synopsis:**
```bash
aws resiliencehub delete-app-version-app-component \
    --app-arn <value> \
    --id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--id` | **Yes** | string | -- | Component ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "appComponent": {
        "name": "string",
        "type": "string",
        "id": "string"
    }
}
```

---

### 2.3 `describe-app-version-app-component`

Describes an AppComponent in a specific app version.

**Synopsis:**
```bash
aws resiliencehub describe-app-version-app-component \
    --app-arn <value> \
    --app-version <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-version` | **Yes** | string | -- | App version |
| `--id` | **Yes** | string | -- | Component ID |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "appComponent": {
        "name": "string",
        "type": "string",
        "id": "string",
        "additionalInfo": {}
    }
}
```

---

### 2.4 `list-app-version-app-components`

Lists AppComponents in a specific app version. **Paginated.**

**Synopsis:**
```bash
aws resiliencehub list-app-version-app-components \
    --app-arn <value> \
    --app-version <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--app-version` | **Yes** | string | -- | App version |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "appComponents": [
        {
            "name": "string",
            "type": "string",
            "id": "string",
            "additionalInfo": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 2.5 `update-app-version-app-component`

Updates an AppComponent in the draft version.

**Synopsis:**
```bash
aws resiliencehub update-app-version-app-component \
    --app-arn <value> \
    --id <value> \
    [--name <value>] \
    [--type <value>] \
    [--additional-info <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-arn` | **Yes** | string | -- | Application ARN |
| `--id` | **Yes** | string | -- | Component ID |
| `--name` | No | string | None | New name |
| `--type` | No | string | None | New type |
| `--additional-info` | No | map | None | Updated additional info |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "appArn": "string",
    "appVersion": "string",
    "appComponent": {
        "name": "string",
        "type": "string",
        "id": "string",
        "additionalInfo": {}
    }
}
```
