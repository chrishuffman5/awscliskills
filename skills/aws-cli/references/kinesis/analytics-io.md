# Analytics I/O

### 7.1 `add-application-input`

Adds a streaming input source to an analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 add-application-input \
    --application-name <value> \
    --current-application-version-id <value> \
    --input <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--current-application-version-id` | **Yes** | long | -- | Current application version ID |
| `--input` | **Yes** | structure | -- | Input configuration (see below) |

**Input Structure:**
```json
{
    "NamePrefix": "string",
    "InputProcessingConfiguration": {
        "InputLambdaProcessor": {
            "ResourceARN": "string"
        }
    },
    "KinesisStreamsInput": {
        "ResourceARN": "string"
    },
    "KinesisFirehoseInput": {
        "ResourceARN": "string"
    },
    "InputParallelism": {
        "Count": 1
    },
    "InputSchema": {
        "RecordFormat": {
            "RecordFormatType": "JSON|CSV",
            "MappingParameters": {
                "JSONMappingParameters": {
                    "RecordRowPath": "string"
                },
                "CSVMappingParameters": {
                    "RecordRowDelimiter": "string",
                    "RecordColumnDelimiter": "string"
                }
            }
        },
        "RecordEncoding": "UTF-8",
        "RecordColumns": [
            {
                "Name": "string",
                "Mapping": "string",
                "SqlType": "string"
            }
        ]
    }
}
```

**Output Schema:**
```json
{
    "ApplicationARN": "string",
    "ApplicationVersionId": "long",
    "InputDescriptions": [
        {
            "InputId": "string",
            "NamePrefix": "string",
            "InAppStreamNames": ["string"],
            "InputProcessingConfigurationDescription": {},
            "KinesisStreamsInputDescription": {
                "ResourceARN": "string"
            },
            "KinesisFirehoseInputDescription": {
                "ResourceARN": "string"
            },
            "InputSchema": {},
            "InputParallelism": {
                "Count": "integer"
            },
            "InputStartingPositionConfiguration": {
                "InputStartingPosition": "NOW|TRIM_HORIZON|LAST_STOPPED_POINT"
            }
        }
    ]
}
```

---

### 7.2 `add-application-output`

Adds an output destination to an analytics application (Kinesis stream, Firehose, or Lambda).

**Synopsis:**
```bash
aws kinesisanalyticsv2 add-application-output \
    --application-name <value> \
    --current-application-version-id <value> \
    --application-output <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--current-application-version-id` | **Yes** | long | -- | Current application version ID |
| `--application-output` | **Yes** | structure | -- | Output configuration (see below) |

**Output Configuration Structure:**
```json
{
    "Name": "string",
    "KinesisStreamsOutput": {
        "ResourceARN": "string"
    },
    "KinesisFirehoseOutput": {
        "ResourceARN": "string"
    },
    "LambdaOutput": {
        "ResourceARN": "string"
    },
    "DestinationSchema": {
        "RecordFormatType": "JSON|CSV"
    }
}
```

**Output Schema:**
```json
{
    "ApplicationARN": "string",
    "ApplicationVersionId": "long",
    "OutputDescriptions": [
        {
            "OutputId": "string",
            "Name": "string",
            "KinesisStreamsOutputDescription": {
                "ResourceARN": "string"
            },
            "KinesisFirehoseOutputDescription": {
                "ResourceARN": "string"
            },
            "LambdaOutputDescription": {
                "ResourceARN": "string"
            },
            "DestinationSchema": {
                "RecordFormatType": "JSON|CSV"
            }
        }
    ]
}
```

---

### 7.3 `delete-application-output`

Removes an output destination from an analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 delete-application-output \
    --application-name <value> \
    --current-application-version-id <value> \
    --output-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--current-application-version-id` | **Yes** | long | -- | Current application version ID |
| `--output-id` | **Yes** | string | -- | ID of the output to remove |

**Output Schema:**
```json
{
    "ApplicationARN": "string",
    "ApplicationVersionId": "long"
}
```

---

### 7.4 `add-application-input-processing-configuration`

Adds a Lambda function as an input preprocessor to an analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 add-application-input-processing-configuration \
    --application-name <value> \
    --current-application-version-id <value> \
    --input-id <value> \
    --input-processing-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--current-application-version-id` | **Yes** | long | -- | Current application version ID |
| `--input-id` | **Yes** | string | -- | Input ID to add preprocessing to |
| `--input-processing-configuration` | **Yes** | structure | -- | Lambda processor config. Shorthand: `InputLambdaProcessor={ResourceARN=string}` |

**Output Schema:**
```json
{
    "ApplicationARN": "string",
    "ApplicationVersionId": "long",
    "InputId": "string",
    "InputProcessingConfigurationDescription": {
        "InputLambdaProcessorDescription": {
            "ResourceARN": "string",
            "RoleARN": "string"
        }
    }
}
```

---

### 7.5 `delete-application-input-processing-configuration`

Removes an input preprocessing configuration from an analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 delete-application-input-processing-configuration \
    --application-name <value> \
    --current-application-version-id <value> \
    --input-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--current-application-version-id` | **Yes** | long | -- | Current application version ID |
| `--input-id` | **Yes** | string | -- | Input ID to remove preprocessing from |

**Output Schema:**
```json
{
    "ApplicationARN": "string",
    "ApplicationVersionId": "long"
}
```

---

### 7.6 `discover-input-schema`

Infers the schema for a streaming source by sampling records.

**Synopsis:**
```bash
aws kinesisanalyticsv2 discover-input-schema \
    --service-execution-role <value> \
    [--resource-arn <value>] \
    [--input-starting-position-configuration <value>] \
    [--s3-configuration <value>] \
    [--input-processing-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-execution-role` | **Yes** | string | -- | IAM role ARN for accessing the source |
| `--resource-arn` | No | string | -- | ARN of the streaming source (Kinesis stream or Firehose) |
| `--input-starting-position-configuration` | No | structure | -- | Starting position: `NOW`, `TRIM_HORIZON`, `LAST_STOPPED_POINT` |
| `--s3-configuration` | No | structure | -- | S3 source config. Shorthand: `BucketARN=string,FileKey=string` |
| `--input-processing-configuration` | No | structure | -- | Lambda processor for input |

**Output Schema:**
```json
{
    "InputSchema": {
        "RecordFormat": {
            "RecordFormatType": "JSON|CSV",
            "MappingParameters": {}
        },
        "RecordEncoding": "string",
        "RecordColumns": [
            {
                "Name": "string",
                "Mapping": "string",
                "SqlType": "string"
            }
        ]
    },
    "ParsedInputRecords": [["string"]],
    "ProcessedInputRecords": ["string"],
    "RawInputRecords": ["string"]
}
```

---

### 7.7 `add-application-reference-data-source`

Adds an S3 reference data source to a SQL analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 add-application-reference-data-source \
    --application-name <value> \
    --current-application-version-id <value> \
    --reference-data-source <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--current-application-version-id` | **Yes** | long | -- | Current application version ID |
| `--reference-data-source` | **Yes** | structure | -- | Reference data source configuration |

**Reference Data Source Structure:**
```json
{
    "TableName": "string",
    "S3ReferenceDataSource": {
        "BucketARN": "string",
        "FileKey": "string"
    },
    "ReferenceSchema": {
        "RecordFormat": {
            "RecordFormatType": "JSON|CSV",
            "MappingParameters": {}
        },
        "RecordEncoding": "string",
        "RecordColumns": [
            {
                "Name": "string",
                "Mapping": "string",
                "SqlType": "string"
            }
        ]
    }
}
```

**Output Schema:**
```json
{
    "ApplicationARN": "string",
    "ApplicationVersionId": "long",
    "ReferenceDataSourceDescriptions": [
        {
            "ReferenceId": "string",
            "TableName": "string",
            "S3ReferenceDataSourceDescription": {
                "BucketARN": "string",
                "FileKey": "string"
            },
            "ReferenceSchema": {}
        }
    ]
}
```

---

### 7.8 `delete-application-reference-data-source`

Removes an S3 reference data source from an analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 delete-application-reference-data-source \
    --application-name <value> \
    --current-application-version-id <value> \
    --reference-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--current-application-version-id` | **Yes** | long | -- | Current application version ID |
| `--reference-id` | **Yes** | string | -- | ID of the reference data source to remove |

**Output Schema:**
```json
{
    "ApplicationARN": "string",
    "ApplicationVersionId": "long"
}
```

---

### 7.9 `add-application-vpc-configuration`

Adds a VPC configuration to a Flink analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 add-application-vpc-configuration \
    --application-name <value> \
    --vpc-configuration <value> \
    [--current-application-version-id <value>] \
    [--conditional-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--vpc-configuration` | **Yes** | structure | -- | VPC config. Shorthand: `SubnetIds=string,string,SecurityGroupIds=string,string` |
| `--current-application-version-id` | No | long | -- | Current application version ID |
| `--conditional-token` | No | string | -- | Conditional update token |

**Output Schema:**
```json
{
    "ApplicationARN": "string",
    "ApplicationVersionId": "long",
    "VpcConfigurationDescription": {
        "VpcConfigurationId": "string",
        "VpcId": "string",
        "SubnetIds": ["string"],
        "SecurityGroupIds": ["string"]
    }
}
```

---

### 7.10 `delete-application-vpc-configuration`

Removes a VPC configuration from a Flink analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 delete-application-vpc-configuration \
    --application-name <value> \
    --vpc-configuration-id <value> \
    [--current-application-version-id <value>] \
    [--conditional-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--vpc-configuration-id` | **Yes** | string | -- | ID of the VPC configuration to remove |
| `--current-application-version-id` | No | long | -- | Current application version ID |
| `--conditional-token` | No | string | -- | Conditional update token |

**Output Schema:**
```json
{
    "ApplicationARN": "string",
    "ApplicationVersionId": "long"
}
```
