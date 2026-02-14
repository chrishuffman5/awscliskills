# Event Stream & Recommenders

### 10.1 `put-event-stream`

Creates or updates an event stream for an application. Sends events to Kinesis Data Stream or Firehose.

**Synopsis:**
```bash
aws pinpoint put-event-stream \
    --application-id <value> \
    --write-event-stream <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--write-event-stream` | **Yes** | structure | -- | Event stream configuration |

**WriteEventStream Fields:**
- `DestinationStreamArn` (string, **required**): ARN of the Kinesis stream or Firehose delivery stream
- `RoleArn` (string, **required**): IAM role ARN for writing to the stream

**Output Schema:**
```json
{
    "EventStream": {
        "ApplicationId": "string",
        "DestinationStreamArn": "string",
        "RoleArn": "string",
        "ExternalId": "string",
        "LastModifiedDate": "string",
        "LastUpdatedBy": "string"
    }
}
```

---

### 10.2 `get-event-stream`

Gets the event stream settings for an application.

**Synopsis:**
```bash
aws pinpoint get-event-stream \
    --application-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |

**Output Schema:** Same as `EventStream` above.

---

### 10.3 `delete-event-stream`

Deletes the event stream for an application.

**Synopsis:**
```bash
aws pinpoint delete-event-stream \
    --application-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |

**Output Schema:** Same as `EventStream`.

---

### 10.4 `create-recommender-configuration`

Creates a recommender model configuration for Amazon Personalize.

**Synopsis:**
```bash
aws pinpoint create-recommender-configuration \
    --create-recommender-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--create-recommender-configuration` | **Yes** | structure | -- | Recommender configuration |

**Configuration Fields:**
- `RecommendationProviderUri` (string, **required**): Amazon Personalize campaign ARN
- `RecommendationProviderRoleArn` (string, **required**): IAM role ARN
- `Name` (string): Display name
- `Description` (string): Description
- `RecommendationProviderIdType` (string): How to retrieve recommendations (`PINPOINT_ENDPOINT_ID` or `PINPOINT_USER_ID`)
- `RecommendationTransformerUri` (string): Lambda function ARN for transforming recommendations
- `RecommendationsDisplayName` (string): Display name for recommendations attribute
- `RecommendationsPerMessage` (integer): Number of recommended items per message (1-5, default 5)
- `Attributes` (map): Custom attributes from recommendations

**Output Schema:**
```json
{
    "RecommenderConfigurationResponse": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "RecommendationProviderUri": "string",
        "RecommendationProviderRoleArn": "string",
        "RecommendationProviderIdType": "string",
        "RecommendationTransformerUri": "string",
        "RecommendationsDisplayName": "string",
        "RecommendationsPerMessage": "integer",
        "Attributes": {},
        "CreationDate": "string",
        "LastModifiedDate": "string"
    }
}
```

---

### 10.5 `get-recommender-configuration`

Gets a recommender configuration.

**Synopsis:**
```bash
aws pinpoint get-recommender-configuration \
    --recommender-id <value>
```

---

### 10.6 `get-recommender-configurations`

Lists recommender configurations.

**Synopsis:**
```bash
aws pinpoint get-recommender-configurations \
    [--page-size <value>] \
    [--token <value>]
```

---

### 10.7 `update-recommender-configuration`

Updates a recommender configuration.

**Synopsis:**
```bash
aws pinpoint update-recommender-configuration \
    --recommender-id <value> \
    --update-recommender-configuration <value>
```

---

### 10.8 `delete-recommender-configuration`

Deletes a recommender configuration.

**Synopsis:**
```bash
aws pinpoint delete-recommender-configuration \
    --recommender-id <value>
```
