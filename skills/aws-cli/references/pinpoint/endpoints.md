# Endpoints

### 7.1 `get-endpoint`

Gets information about an endpoint.

**Synopsis:**
```bash
aws pinpoint get-endpoint \
    --application-id <value> \
    --endpoint-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--endpoint-id` | **Yes** | string | -- | Endpoint ID |

**Output Schema:**
```json
{
    "EndpointResponse": {
        "ApplicationId": "string",
        "Id": "string",
        "ChannelType": "PUSH|GCM|APNS|APNS_SANDBOX|APNS_VOIP|ADM|SMS|VOICE|EMAIL|BAIDU|CUSTOM|IN_APP",
        "Address": "string",
        "EndpointStatus": "ACTIVE|INACTIVE",
        "OptOut": "ALL|NONE",
        "CreationDate": "string",
        "EffectiveDate": "string",
        "Attributes": {"string": ["string"]},
        "Metrics": {"string": "double"},
        "Demographic": {
            "AppVersion": "string",
            "Locale": "string",
            "Make": "string",
            "Model": "string",
            "ModelVersion": "string",
            "Platform": "string",
            "PlatformVersion": "string",
            "Timezone": "string"
        },
        "Location": {
            "City": "string",
            "Country": "string",
            "Latitude": "double",
            "Longitude": "double",
            "PostalCode": "string",
            "Region": "string"
        },
        "User": {
            "UserAttributes": {"string": ["string"]},
            "UserId": "string"
        },
        "RequestId": "string",
        "CohortId": "string"
    }
}
```

---

### 7.2 `update-endpoint`

Creates or updates an endpoint.

**Synopsis:**
```bash
aws pinpoint update-endpoint \
    --application-id <value> \
    --endpoint-id <value> \
    --endpoint-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--endpoint-id` | **Yes** | string | -- | Endpoint ID |
| `--endpoint-request` | **Yes** | structure | -- | Endpoint data (JSON recommended) |

**EndpointRequest Key Fields:**
- `Address` (string): Endpoint address (email, phone, push token)
- `ChannelType` (string): Channel type
- `Attributes` (map): Custom attributes (key -> string list)
- `Demographic` (structure): Device demographics
- `EffectiveDate` (string): ISO 8601 timestamp
- `EndpointStatus` (string): `ACTIVE` or `INACTIVE`
- `Location` (structure): Location data
- `Metrics` (map): Custom metrics (key -> double)
- `OptOut` (string): `ALL` or `NONE`
- `RequestId` (string): Request ID for idempotency
- `User` (structure): User data with `UserId` and `UserAttributes`

**Output Schema:**
```json
{
    "MessageBody": {
        "Message": "string",
        "RequestID": "string"
    }
}
```

---

### 7.3 `delete-endpoint`

Deletes an endpoint.

**Synopsis:**
```bash
aws pinpoint delete-endpoint \
    --application-id <value> \
    --endpoint-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--endpoint-id` | **Yes** | string | -- | Endpoint ID |

**Output Schema:** Same as `EndpointResponse`.

---

### 7.4 `get-user-endpoints`

Gets all endpoints associated with a user.

**Synopsis:**
```bash
aws pinpoint get-user-endpoints \
    --application-id <value> \
    --user-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--user-id` | **Yes** | string | -- | User ID |

**Output Schema:**
```json
{
    "EndpointsResponse": {
        "Item": [{"EndpointResponse": "..."}]
    }
}
```

---

### 7.5 `delete-user-endpoints`

Deletes all endpoints associated with a user.

**Synopsis:**
```bash
aws pinpoint delete-user-endpoints \
    --application-id <value> \
    --user-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--user-id` | **Yes** | string | -- | User ID |

**Output Schema:** Same as `EndpointsResponse`.

---

### 7.6 `update-endpoints-batch`

Creates or updates up to 100 endpoints in a single batch request.

**Synopsis:**
```bash
aws pinpoint update-endpoints-batch \
    --application-id <value> \
    --endpoint-batch-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--endpoint-batch-request` | **Yes** | structure | -- | Batch of endpoint items. Contains `Item` (list of EndpointBatchItem, max 100) |

**EndpointBatchItem** has the same fields as EndpointRequest plus `Id` (endpoint ID).

**Output Schema:**
```json
{
    "MessageBody": {
        "Message": "string",
        "RequestID": "string"
    }
}
```
