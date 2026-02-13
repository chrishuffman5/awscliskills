# Functions

### 1.1 `create-function`

Creates a Lambda function. You can create a function from a deployment package (zip) or a container image.

**Synopsis:**
```bash
aws lambda create-function \
    --function-name <value> \
    --role <value> \
    [--runtime <value>] \
    [--handler <value>] \
    [--code <value>] \
    [--zip-file <value>] \
    [--description <value>] \
    [--timeout <value>] \
    [--memory-size <value>] \
    [--publish | --no-publish] \
    [--vpc-config <value>] \
    [--package-type <value>] \
    [--dead-letter-config <value>] \
    [--environment <value>] \
    [--kms-key-arn <value>] \
    [--tracing-config <value>] \
    [--tags <value>] \
    [--layers <value>] \
    [--file-system-configs <value>] \
    [--image-config <value>] \
    [--code-signing-config-arn <value>] \
    [--architectures <value>] \
    [--ephemeral-storage <value>] \
    [--snap-start <value>] \
    [--logging-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name (1-140 chars). Accepts name, ARN, or partial ARN |
| `--role` | **Yes** | string | -- | Execution role ARN |
| `--runtime` | Cond. | string | -- | Runtime identifier (required for Zip). Values: `python3.12`, `python3.13`, `nodejs20.x`, `nodejs22.x`, `java21`, `dotnet8`, `ruby3.3`, `provided.al2023`, etc. |
| `--handler` | Cond. | string | -- | Handler method (required for Zip). Format: `file.method` (e.g., `index.handler`) |
| `--code` | No | structure | -- | Code location. Shorthand: `S3Bucket=string,S3Key=string,S3ObjectVersion=string,ImageUri=string,SourceKMSKeyArn=string` |
| `--zip-file` | No | blob | -- | Path to zip deployment package (e.g., `fileb://function.zip`) |
| `--description` | No | string | `""` | Description (0-256 chars) |
| `--timeout` | No | integer | `3` | Execution timeout in seconds (1-900) |
| `--memory-size` | No | integer | `128` | Memory in MB (128-10240, 1 MB increments) |
| `--publish` / `--no-publish` | No | boolean | `false` | Publish version 1 on creation |
| `--vpc-config` | No | structure | -- | VPC config. Shorthand: `SubnetIds=string,string,SecurityGroupIds=string,string,Ipv6AllowedForDualStack=boolean` |
| `--package-type` | No | string | `Zip` | Values: `Zip`, `Image` |
| `--dead-letter-config` | No | structure | -- | DLQ config. Shorthand: `TargetArn=string` (SQS or SNS ARN) |
| `--environment` | No | structure | -- | Environment variables. Shorthand: `Variables={Key1=Value1,Key2=Value2}` |
| `--kms-key-arn` | No | string | -- | KMS key for encrypting environment variables |
| `--tracing-config` | No | structure | -- | X-Ray tracing. Shorthand: `Mode=Active\|PassThrough` |
| `--tags` | No | map | -- | Tags. Shorthand: `Key1=Value1,Key2=Value2` |
| `--layers` | No | list | -- | Layer ARNs with version (up to 5) |
| `--file-system-configs` | No | list | -- | EFS config. Shorthand: `Arn=string,LocalMountPath=string` |
| `--image-config` | No | structure | -- | Container image overrides. Shorthand: `EntryPoint=string,string,Command=string,string,WorkingDirectory=string` |
| `--code-signing-config-arn` | No | string | -- | Code signing configuration ARN |
| `--architectures` | No | list | `["x86_64"]` | Values: `x86_64`, `arm64` |
| `--ephemeral-storage` | No | structure | `512` | `/tmp` storage in MB (512-10240). Shorthand: `Size=integer` |
| `--snap-start` | No | structure | -- | SnapStart config. Shorthand: `ApplyOn=PublishedVersions\|None` |
| `--logging-config` | No | structure | -- | CloudWatch logging. Shorthand: `LogFormat=JSON\|Text,ApplicationLogLevel=string,SystemLogLevel=string,LogGroup=string` |

**Output Schema:**
```json
{
    "FunctionName": "string",
    "FunctionArn": "string",
    "Runtime": "string",
    "Role": "string",
    "Handler": "string",
    "CodeSize": "long",
    "Description": "string",
    "Timeout": "integer",
    "MemorySize": "integer",
    "LastModified": "string",
    "CodeSha256": "string",
    "Version": "string",
    "VpcConfig": {
        "SubnetIds": ["string"],
        "SecurityGroupIds": ["string"],
        "VpcId": "string",
        "Ipv6AllowedForDualStack": true|false
    },
    "DeadLetterConfig": {
        "TargetArn": "string"
    },
    "Environment": {
        "Variables": {"string": "string"},
        "Error": {"ErrorCode": "string", "Message": "string"}
    },
    "KMSKeyArn": "string",
    "TracingConfig": {
        "Mode": "Active|PassThrough"
    },
    "MasterArn": "string",
    "RevisionId": "string",
    "Layers": [
        {
            "Arn": "string",
            "CodeSize": "long",
            "SigningProfileVersionArn": "string",
            "SigningJobArn": "string"
        }
    ],
    "State": "Pending|Active|Inactive|Failed",
    "StateReason": "string",
    "StateReasonCode": "string",
    "LastUpdateStatus": "Successful|Failed|InProgress",
    "LastUpdateStatusReason": "string",
    "LastUpdateStatusReasonCode": "string",
    "FileSystemConfigs": [
        {"Arn": "string", "LocalMountPath": "string"}
    ],
    "PackageType": "Zip|Image",
    "ImageConfigResponse": {
        "ImageConfig": {
            "EntryPoint": ["string"],
            "Command": ["string"],
            "WorkingDirectory": "string"
        },
        "Error": {"ErrorCode": "string", "Message": "string"}
    },
    "SigningProfileVersionArn": "string",
    "SigningJobArn": "string",
    "Architectures": ["x86_64|arm64"],
    "EphemeralStorage": {"Size": "integer"},
    "SnapStart": {
        "ApplyOn": "PublishedVersions|None",
        "OptimizationStatus": "On|Off"
    },
    "RuntimeVersionConfig": {
        "RuntimeVersionArn": "string",
        "Error": {"ErrorCode": "string", "Message": "string"}
    },
    "LoggingConfig": {
        "LogFormat": "JSON|Text",
        "ApplicationLogLevel": "TRACE|DEBUG|INFO|WARN|ERROR|FATAL",
        "SystemLogLevel": "DEBUG|INFO|WARN",
        "LogGroup": "string"
    }
}
```

---

### 1.2 `delete-function`

Deletes a Lambda function. To delete a specific version, use `--qualifier`.

**Synopsis:**
```bash
aws lambda delete-function \
    --function-name <value> \
    [--qualifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-256 chars) |
| `--qualifier` | No | string | -- | Version to delete (1-128 chars). Cannot delete version referenced by an alias |

**Output:** None on success.

---

### 1.3 `get-function`

Returns the function's configuration, code location (presigned URL), tags, and concurrency setting.

**Synopsis:**
```bash
aws lambda get-function \
    --function-name <value> \
    [--qualifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name, ARN, or partial ARN (1-256 chars) |
| `--qualifier` | No | string | -- | Version or alias name (1-128 chars) |

**Output Schema:**
```json
{
    "Configuration": {
        "FunctionName": "string",
        "FunctionArn": "string",
        "Runtime": "string",
        "Role": "string",
        "Handler": "string",
        "CodeSize": "long",
        "Description": "string",
        "Timeout": "integer",
        "MemorySize": "integer",
        "LastModified": "string",
        "CodeSha256": "string",
        "Version": "string",
        "VpcConfig": {
            "SubnetIds": ["string"],
            "SecurityGroupIds": ["string"],
            "VpcId": "string"
        },
        "DeadLetterConfig": {"TargetArn": "string"},
        "Environment": {
            "Variables": {"string": "string"},
            "Error": {"ErrorCode": "string", "Message": "string"}
        },
        "KMSKeyArn": "string",
        "TracingConfig": {"Mode": "Active|PassThrough"},
        "MasterArn": "string",
        "RevisionId": "string",
        "Layers": [{"Arn": "string", "CodeSize": "long"}],
        "State": "Pending|Active|Inactive|Failed",
        "StateReason": "string",
        "LastUpdateStatus": "Successful|Failed|InProgress",
        "PackageType": "Zip|Image",
        "Architectures": ["x86_64|arm64"],
        "EphemeralStorage": {"Size": "integer"},
        "LoggingConfig": {
            "LogFormat": "JSON|Text",
            "LogGroup": "string"
        }
    },
    "Code": {
        "RepositoryType": "string",
        "Location": "string",
        "ImageUri": "string",
        "ResolvedImageUri": "string"
    },
    "Tags": {"string": "string"},
    "Concurrency": {
        "ReservedConcurrentExecutions": "integer"
    }
}
```

---

### 1.4 `get-function-configuration`

Returns only the function's configuration (no code location or tags).

**Synopsis:**
```bash
aws lambda get-function-configuration \
    --function-name <value> \
    [--qualifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name, ARN, or partial ARN (1-256 chars) |
| `--qualifier` | No | string | -- | Version or alias name (1-128 chars) |

**Output Schema:** Same as the `Configuration` object in `get-function` output.

---

### 1.5 `list-functions`

Returns a list of Lambda functions. **Paginated operation.**

**Synopsis:**
```bash
aws lambda list-functions \
    [--master-region <value>] \
    [--function-version <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--master-region` | No | string | -- | For Lambda@Edge, region of the master function. Use `ALL` for all regions |
| `--function-version` | No | string | -- | Set to `ALL` to include all published versions |
| `--starting-token` | No | string | -- | Pagination token from previous response |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Functions": [
        {
            "FunctionName": "string",
            "FunctionArn": "string",
            "Runtime": "string",
            "Role": "string",
            "Handler": "string",
            "CodeSize": "long",
            "Description": "string",
            "Timeout": "integer",
            "MemorySize": "integer",
            "LastModified": "string",
            "CodeSha256": "string",
            "Version": "string",
            "VpcConfig": {"SubnetIds": ["string"], "SecurityGroupIds": ["string"], "VpcId": "string"},
            "DeadLetterConfig": {"TargetArn": "string"},
            "Environment": {"Variables": {"string": "string"}},
            "TracingConfig": {"Mode": "Active|PassThrough"},
            "Layers": [{"Arn": "string", "CodeSize": "long"}],
            "State": "Pending|Active|Inactive|Failed",
            "PackageType": "Zip|Image",
            "Architectures": ["x86_64|arm64"],
            "EphemeralStorage": {"Size": "integer"},
            "LoggingConfig": {"LogFormat": "JSON|Text", "LogGroup": "string"}
        }
    ],
    "NextMarker": "string"
}
```

---

### 1.6 `update-function-code`

Updates a function's code. For zip packages, provide `--zip-file` or S3 location. For container images, provide `--image-uri` in `--code`.

**Synopsis:**
```bash
aws lambda update-function-code \
    --function-name <value> \
    [--zip-file <value>] \
    [--s3-bucket <value>] \
    [--s3-key <value>] \
    [--s3-object-version <value>] \
    [--image-uri <value>] \
    [--publish | --no-publish] \
    [--dry-run | --no-dry-run] \
    [--revision-id <value>] \
    [--architectures <value>] \
    [--source-kms-key-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--zip-file` | No | blob | -- | Zip file path (e.g., `fileb://function.zip`) |
| `--s3-bucket` | No | string | -- | S3 bucket containing deployment package (3-63 chars) |
| `--s3-key` | No | string | -- | S3 object key (1-1024 chars) |
| `--s3-object-version` | No | string | -- | S3 object version (for versioned buckets) |
| `--image-uri` | No | string | -- | ECR container image URI |
| `--publish` / `--no-publish` | No | boolean | `false` | Publish a new version after update |
| `--dry-run` / `--no-dry-run` | No | boolean | `false` | Validate without modifying |
| `--revision-id` | No | string | -- | Only update if revision ID matches |
| `--architectures` | No | list | -- | Values: `x86_64`, `arm64` |
| `--source-kms-key-arn` | No | string | -- | KMS key ARN for decrypting source |

**Output Schema:** Same as `create-function` output (FunctionConfiguration).

---

### 1.7 `update-function-configuration`

Modifies a function's configuration (runtime, memory, timeout, environment, etc.).

**Synopsis:**
```bash
aws lambda update-function-configuration \
    --function-name <value> \
    [--role <value>] \
    [--handler <value>] \
    [--description <value>] \
    [--timeout <value>] \
    [--memory-size <value>] \
    [--vpc-config <value>] \
    [--environment <value>] \
    [--runtime <value>] \
    [--dead-letter-config <value>] \
    [--kms-key-arn <value>] \
    [--tracing-config <value>] \
    [--revision-id <value>] \
    [--layers <value>] \
    [--file-system-configs <value>] \
    [--image-config <value>] \
    [--ephemeral-storage <value>] \
    [--snap-start <value>] \
    [--logging-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--role` | No | string | -- | Execution role ARN |
| `--handler` | No | string | -- | Handler method (0-128 chars) |
| `--description` | No | string | -- | Description (0-256 chars) |
| `--timeout` | No | integer | -- | Timeout in seconds (1-900) |
| `--memory-size` | No | integer | -- | Memory in MB (128-10240) |
| `--vpc-config` | No | structure | -- | VPC config. Shorthand: `SubnetIds=string,string,SecurityGroupIds=string,string` |
| `--environment` | No | structure | -- | Env vars. Shorthand: `Variables={Key=Value,Key2=Value2}` |
| `--runtime` | No | string | -- | Runtime identifier |
| `--dead-letter-config` | No | structure | -- | DLQ config. Shorthand: `TargetArn=string` |
| `--kms-key-arn` | No | string | -- | KMS key ARN |
| `--tracing-config` | No | structure | -- | X-Ray tracing. Shorthand: `Mode=Active\|PassThrough` |
| `--revision-id` | No | string | -- | Only update if revision ID matches |
| `--layers` | No | list | -- | Layer ARNs with version (up to 5) |
| `--file-system-configs` | No | list | -- | EFS config |
| `--image-config` | No | structure | -- | Container image overrides |
| `--ephemeral-storage` | No | structure | -- | `/tmp` storage in MB (512-10240) |
| `--snap-start` | No | structure | -- | SnapStart config |
| `--logging-config` | No | structure | -- | CloudWatch logging config |

**Output Schema:** Same as `create-function` output (FunctionConfiguration).

---

### 1.8 `put-function-event-invoke-config`

Configures options for asynchronous invocation on a function, version, or alias.

**Synopsis:**
```bash
aws lambda put-function-event-invoke-config \
    --function-name <value> \
    [--qualifier <value>] \
    [--maximum-retry-attempts <value>] \
    [--maximum-event-age-in-seconds <value>] \
    [--destination-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--qualifier` | No | string | -- | Version or alias (1-128 chars) |
| `--maximum-retry-attempts` | No | integer | `2` | Max retries (0-2) |
| `--maximum-event-age-in-seconds` | No | integer | `21600` | Max event age (60-21600, i.e. 1 min to 6 hours) |
| `--destination-config` | No | structure | -- | Destinations for success/failure. Shorthand: `OnSuccess={Destination=string},OnFailure={Destination=string}` |

**Output Schema:**
```json
{
    "LastModified": "timestamp",
    "FunctionArn": "string",
    "MaximumRetryAttempts": "integer",
    "MaximumEventAgeInSeconds": "integer",
    "DestinationConfig": {
        "OnSuccess": {"Destination": "string"},
        "OnFailure": {"Destination": "string"}
    }
}
```

---

### 1.9 `get-function-event-invoke-config`

Retrieves the async invocation configuration for a function, version, or alias.

**Synopsis:**
```bash
aws lambda get-function-event-invoke-config \
    --function-name <value> \
    [--qualifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--qualifier` | No | string | -- | Version or alias (1-128 chars) |

**Output Schema:** Same as `put-function-event-invoke-config`.

---

### 1.10 `update-function-event-invoke-config`

Updates async invocation configuration. Same parameters as `put-function-event-invoke-config`.

**Synopsis:**
```bash
aws lambda update-function-event-invoke-config \
    --function-name <value> \
    [--qualifier <value>] \
    [--maximum-retry-attempts <value>] \
    [--maximum-event-age-in-seconds <value>] \
    [--destination-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `put-function-event-invoke-config`.

**Output Schema:** Same as `put-function-event-invoke-config`.

---

### 1.11 `delete-function-event-invoke-config`

Deletes the async invocation configuration for a function, version, or alias.

**Synopsis:**
```bash
aws lambda delete-function-event-invoke-config \
    --function-name <value> \
    [--qualifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--qualifier` | No | string | -- | Version or alias (1-128 chars) |

**Output:** None on success.

---

### 1.12 `list-function-event-invoke-configs`

Lists async invocation configurations for a function. **Paginated operation.**

**Synopsis:**
```bash
aws lambda list-function-event-invoke-configs \
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
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "FunctionEventInvokeConfigs": [
        {
            "LastModified": "timestamp",
            "FunctionArn": "string",
            "MaximumRetryAttempts": "integer",
            "MaximumEventAgeInSeconds": "integer",
            "DestinationConfig": {
                "OnSuccess": {"Destination": "string"},
                "OnFailure": {"Destination": "string"}
            }
        }
    ],
    "NextMarker": "string"
}
```

---

### 1.13 `get-function-recursion-config`

Returns the recursion detection configuration for a function.

**Synopsis:**
```bash
aws lambda get-function-recursion-config \
    --function-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |

**Output Schema:**
```json
{
    "RecursiveLoop": "Terminate|Allow"
}
```

---

### 1.14 `put-function-recursion-config`

Sets the recursion detection configuration for a function.

**Synopsis:**
```bash
aws lambda put-function-recursion-config \
    --function-name <value> \
    --recursive-loop <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |
| `--recursive-loop` | **Yes** | string | -- | Values: `Terminate`, `Allow` |

**Output Schema:**
```json
{
    "RecursiveLoop": "Terminate|Allow"
}
```

---
