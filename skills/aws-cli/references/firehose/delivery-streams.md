# Delivery Streams

### 1.1 `create-delivery-stream`

Creates a new Firehose delivery stream. The operation is asynchronous — the stream status starts as `CREATING` and transitions to `ACTIVE`. Limit: 5,000 streams per region.

**Synopsis:**
```bash
aws firehose create-delivery-stream \
    --delivery-stream-name <value> \
    [--delivery-stream-type <value>] \
    [--direct-put-source-configuration <value>] \
    [--kinesis-stream-source-configuration <value>] \
    [--msk-source-configuration <value>] \
    [--database-source-configuration <value>] \
    [--delivery-stream-encryption-configuration-input <value>] \
    [--extended-s3-destination-configuration <value>] \
    [--redshift-destination-configuration <value>] \
    [--amazonopensearchservice-destination-configuration <value>] \
    [--amazon-open-search-serverless-destination-configuration <value>] \
    [--splunk-destination-configuration <value>] \
    [--http-endpoint-destination-configuration <value>] \
    [--snowflake-destination-configuration <value>] \
    [--iceberg-destination-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-stream-name` | **Yes** | string | -- | Stream name (1-64 chars, pattern: `[a-zA-Z0-9_.-]+`) |
| `--delivery-stream-type` | No | string | `DirectPut` | `DirectPut`, `KinesisStreamAsSource`, `MSKAsSource`, `DatabaseAsSource` |
| `--direct-put-source-configuration` | No | structure | None | Direct PUT config with throughput hint |
| `--kinesis-stream-source-configuration` | No | structure | None | Kinesis source (requires `KinesisStreamARN`, `RoleARN`) |
| `--msk-source-configuration` | No | structure | None | MSK source configuration |
| `--database-source-configuration` | No | structure | None | Database CDC source configuration |
| `--delivery-stream-encryption-configuration-input` | No | structure | None | SSE config: `KeyType=AWS_OWNED_CMK\|CUSTOMER_MANAGED_CMK` |
| `--extended-s3-destination-configuration` | No | structure | None | S3 destination with transforms and format conversion |
| `--redshift-destination-configuration` | No | structure | None | Redshift destination via S3 COPY |
| `--amazonopensearchservice-destination-configuration` | No | structure | None | OpenSearch Service destination |
| `--amazon-open-search-serverless-destination-configuration` | No | structure | None | OpenSearch Serverless destination |
| `--splunk-destination-configuration` | No | structure | None | Splunk HEC destination |
| `--http-endpoint-destination-configuration` | No | structure | None | HTTP endpoint destination |
| `--snowflake-destination-configuration` | No | structure | None | Snowflake destination |
| `--iceberg-destination-configuration` | No | structure | None | Apache Iceberg table destination |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Extended S3 Destination Structure:**
```json
{
    "RoleARN": "string",
    "BucketARN": "string",
    "Prefix": "string",
    "ErrorOutputPrefix": "string",
    "BufferingHints": {
        "SizeInMBs": 128,
        "IntervalInSeconds": 60
    },
    "CompressionFormat": "UNCOMPRESSED|GZIP|ZIP|Snappy|HADOOP_SNAPPY",
    "EncryptionConfiguration": {
        "KMSEncryptionConfig": {
            "AWSKMSKeyARN": "string"
        }
    },
    "CloudWatchLoggingOptions": {
        "Enabled": true,
        "LogGroupName": "string",
        "LogStreamName": "string"
    },
    "ProcessingConfiguration": {
        "Enabled": true,
        "Processors": [
            {
                "Type": "Lambda|RecordDeAggregation|Decompression|MetadataExtraction|AppendDelimiterToRecord",
                "Parameters": [
                    {
                        "ParameterName": "LambdaArn|NumberOfRetries|RoleArn|BufferSizeInMBs|BufferIntervalInSeconds|MetadataExtractionQuery|JsonParsingEngine|Delimiter",
                        "ParameterValue": "string"
                    }
                ]
            }
        ]
    },
    "S3BackupMode": "Disabled|Enabled",
    "S3BackupConfiguration": {},
    "DataFormatConversionConfiguration": {
        "Enabled": true,
        "SchemaConfiguration": {
            "RoleARN": "string",
            "DatabaseName": "string",
            "TableName": "string",
            "Region": "string",
            "VersionId": "LATEST"
        },
        "InputFormatConfiguration": {
            "Deserializer": {
                "OpenXJsonSerDe": {},
                "HiveJsonSerDe": {}
            }
        },
        "OutputFormatConfiguration": {
            "Serializer": {
                "ParquetSerDe": {"Compression": "SNAPPY"},
                "OrcSerDe": {"Compression": "SNAPPY"}
            }
        }
    },
    "DynamicPartitioningConfiguration": {
        "Enabled": true,
        "RetryOptions": {"DurationInSeconds": 300}
    },
    "FileExtension": "string",
    "CustomTimeZone": "string"
}
```

**Output Schema:**
```json
{
    "DeliveryStreamARN": "string"
}
```

---

### 1.2 `delete-delivery-stream`

Deletes a delivery stream. If the stream is `ACTIVE`, it transitions to `DELETING`.

**Synopsis:**
```bash
aws firehose delete-delivery-stream \
    --delivery-stream-name <value> \
    [--allow-force-delete | --no-allow-force-delete] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-stream-name` | **Yes** | string | -- | Name of the stream to delete |
| `--allow-force-delete` | No | boolean | false | Force delete even if stream is not in `ACTIVE` or `DELETING_FAILED` state |

**Output:** None

---

### 1.3 `describe-delivery-stream`

Returns detailed information about a delivery stream, including destination configuration.

**Synopsis:**
```bash
aws firehose describe-delivery-stream \
    --delivery-stream-name <value> \
    [--limit <value>] \
    [--exclusive-start-destination-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-stream-name` | **Yes** | string | -- | Name of the stream |
| `--limit` | No | integer | 10 | Max destinations to return (1-10000) |
| `--exclusive-start-destination-id` | No | string | -- | Destination ID to start listing after |

**Output Schema:**
```json
{
    "DeliveryStreamDescription": {
        "DeliveryStreamName": "string",
        "DeliveryStreamARN": "string",
        "DeliveryStreamStatus": "CREATING|CREATING_FAILED|DELETING|DELETING_FAILED|ACTIVE",
        "FailureDescription": {
            "Type": "string",
            "Details": "string"
        },
        "DeliveryStreamEncryptionConfiguration": {
            "KeyARN": "string",
            "KeyType": "AWS_OWNED_CMK|CUSTOMER_MANAGED_CMK",
            "Status": "ENABLED|ENABLING|ENABLING_FAILED|DISABLED|DISABLING|DISABLING_FAILED",
            "FailureDescription": {}
        },
        "DeliveryStreamType": "DirectPut|KinesisStreamAsSource|MSKAsSource|DatabaseAsSource",
        "VersionId": "string",
        "CreateTimestamp": "timestamp",
        "LastUpdateTimestamp": "timestamp",
        "Source": {
            "KinesisStreamSourceDescription": {
                "KinesisStreamARN": "string",
                "RoleARN": "string",
                "DeliveryStartTimestamp": "timestamp"
            },
            "MSKSourceDescription": {
                "MSKClusterARN": "string",
                "TopicName": "string"
            },
            "DatabaseSourceDescription": {}
        },
        "Destinations": [
            {
                "DestinationId": "string",
                "ExtendedS3DestinationDescription": {},
                "RedshiftDestinationDescription": {},
                "ElasticsearchDestinationDescription": {},
                "AmazonopensearchserviceDestinationDescription": {},
                "SplunkDestinationDescription": {},
                "HttpEndpointDestinationDescription": {},
                "SnowflakeDestinationDescription": {},
                "AmazonOpenSearchServerlessDestinationDescription": {},
                "IcebergDestinationDescription": {}
            }
        ],
        "HasMoreDestinations": "boolean"
    }
}
```

---

### 1.4 `list-delivery-streams`

Lists delivery streams in the account. Manual pagination required.

**Synopsis:**
```bash
aws firehose list-delivery-streams \
    [--limit <value>] \
    [--delivery-stream-type <value>] \
    [--exclusive-start-delivery-stream-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--limit` | No | integer | 10 | Max streams to return (1-10000) |
| `--delivery-stream-type` | No | string | -- | Filter by type: `DirectPut`, `KinesisStreamAsSource`, `MSKAsSource`, `DatabaseAsSource` |
| `--exclusive-start-delivery-stream-name` | No | string | -- | Start listing after this stream name |

**Output Schema:**
```json
{
    "DeliveryStreamNames": ["string"],
    "HasMoreDeliveryStreams": "boolean"
}
```

---

### 1.5 `update-destination`

Updates the destination configuration for a delivery stream. The stream remains active during updates.

**Synopsis:**
```bash
aws firehose update-destination \
    --delivery-stream-name <value> \
    --current-delivery-stream-version-id <value> \
    --destination-id <value> \
    [--extended-s3-destination-update <value>] \
    [--redshift-destination-update <value>] \
    [--amazonopensearchservice-destination-update <value>] \
    [--amazon-open-search-serverless-destination-update <value>] \
    [--splunk-destination-update <value>] \
    [--http-endpoint-destination-update <value>] \
    [--snowflake-destination-update <value>] \
    [--iceberg-destination-update <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-stream-name` | **Yes** | string | -- | Name of the stream |
| `--current-delivery-stream-version-id` | **Yes** | string | -- | Version ID from `describe-delivery-stream` |
| `--destination-id` | **Yes** | string | -- | Destination ID to update |
| `--extended-s3-destination-update` | No | structure | None | S3 destination updates |
| `--redshift-destination-update` | No | structure | None | Redshift destination updates |
| `--amazonopensearchservice-destination-update` | No | structure | None | OpenSearch destination updates |
| `--amazon-open-search-serverless-destination-update` | No | structure | None | OpenSearch Serverless updates |
| `--splunk-destination-update` | No | structure | None | Splunk destination updates |
| `--http-endpoint-destination-update` | No | structure | None | HTTP endpoint updates |
| `--snowflake-destination-update` | No | structure | None | Snowflake destination updates |
| `--iceberg-destination-update` | No | structure | None | Iceberg destination updates |

**Output:** None

---

### 1.6 `start-delivery-stream-encryption`

Enables server-side encryption (SSE) for a delivery stream. Asynchronous operation.

**Synopsis:**
```bash
aws firehose start-delivery-stream-encryption \
    --delivery-stream-name <value> \
    [--delivery-stream-encryption-configuration-input <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-stream-name` | **Yes** | string | -- | Name of the stream |
| `--delivery-stream-encryption-configuration-input` | No | structure | None | Encryption config. Shorthand: `KeyARN=string,KeyType=AWS_OWNED_CMK\|CUSTOMER_MANAGED_CMK` |

**Output:** None

---

### 1.7 `stop-delivery-stream-encryption`

Disables server-side encryption (SSE) for a delivery stream. Asynchronous operation.

**Synopsis:**
```bash
aws firehose stop-delivery-stream-encryption \
    --delivery-stream-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delivery-stream-name` | **Yes** | string | -- | Name of the stream |

**Output:** None
