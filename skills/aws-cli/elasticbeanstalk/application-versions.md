# Application Versions

### 2.1 `create-application-version`

Creates an application version for the specified application. Once created, you can deploy the version to an environment.

**Synopsis:**
```bash
aws elasticbeanstalk create-application-version \
    --application-name <value> \
    --version-label <value> \
    [--description <value>] \
    [--source-build-information <value>] \
    [--source-bundle <value>] \
    [--build-configuration <value>] \
    [--auto-create-application | --no-auto-create-application] \
    [--process | --no-process] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--version-label` | **Yes** | string | -- | Unique label for this version (1-100 chars) |
| `--description` | No | string | -- | Description of the version |
| `--source-bundle` | No | structure | None | S3 location of the source bundle. Shorthand: `S3Bucket=string,S3Key=string` |
| `--source-build-information` | No | structure | None | Build information for CodeBuild. Shorthand: `SourceType=string,SourceRepository=string,SourceLocation=string` |
| `--build-configuration` | No | structure | None | CodeBuild build configuration |
| `--auto-create-application` | No | boolean | false | Create the application if it does not exist |
| `--process` | No | boolean | false | Pre-process and validate the source bundle |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "ApplicationVersion": {
        "ApplicationVersionArn": "string",
        "ApplicationName": "string",
        "Description": "string",
        "VersionLabel": "string",
        "SourceBuildInformation": {
            "SourceType": "Git|Zip",
            "SourceRepository": "CodeCommit|S3",
            "SourceLocation": "string"
        },
        "BuildArn": "string",
        "SourceBundle": {
            "S3Bucket": "string",
            "S3Key": "string"
        },
        "DateCreated": "timestamp",
        "DateUpdated": "timestamp",
        "Status": "Processed|Unprocessed|Failed|Processing|Building"
    }
}
```

---

### 2.2 `describe-application-versions`

Retrieves a list of application versions. **Paginated operation.**

**Synopsis:**
```bash
aws elasticbeanstalk describe-application-versions \
    [--application-name <value>] \
    [--version-labels <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | No | string | -- | Filter by application name |
| `--version-labels` | No | list(string) | None | Filter by version labels |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ApplicationVersions": [
        {
            "ApplicationVersionArn": "string",
            "ApplicationName": "string",
            "Description": "string",
            "VersionLabel": "string",
            "SourceBuildInformation": {},
            "BuildArn": "string",
            "SourceBundle": {
                "S3Bucket": "string",
                "S3Key": "string"
            },
            "DateCreated": "timestamp",
            "DateUpdated": "timestamp",
            "Status": "Processed|Unprocessed|Failed|Processing|Building"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.3 `update-application-version`

Updates the specified application version to have the specified properties.

**Synopsis:**
```bash
aws elasticbeanstalk update-application-version \
    --application-name <value> \
    --version-label <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--version-label` | **Yes** | string | -- | Version label to update |
| `--description` | No | string | -- | Updated description |

**Output Schema:**
```json
{
    "ApplicationVersion": {
        "ApplicationVersionArn": "string",
        "ApplicationName": "string",
        "Description": "string",
        "VersionLabel": "string",
        "SourceBundle": {},
        "DateCreated": "timestamp",
        "DateUpdated": "timestamp",
        "Status": "string"
    }
}
```

---

### 2.4 `delete-application-version`

Deletes the specified version from the specified application.

**Synopsis:**
```bash
aws elasticbeanstalk delete-application-version \
    --application-name <value> \
    --version-label <value> \
    [--delete-source-bundle | --no-delete-source-bundle] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--version-label` | **Yes** | string | -- | Version label to delete |
| `--delete-source-bundle` | No | boolean | false | Also delete the source bundle from S3 |

**Output Schema:**
```json
{}
```
