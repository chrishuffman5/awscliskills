# Platforms

### 6.1 `create-platform-version`

Creates a new version of a custom platform.

**Synopsis:**
```bash
aws elasticbeanstalk create-platform-version \
    --platform-name <value> \
    --platform-version <value> \
    --platform-definition-bundle <value> \
    [--environment-name <value>] \
    [--option-settings <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--platform-name` | **Yes** | string | -- | Name of the custom platform |
| `--platform-version` | **Yes** | string | -- | Version number (e.g., `1.0.0`) |
| `--platform-definition-bundle` | **Yes** | structure | -- | S3 location. Shorthand: `S3Bucket=string,S3Key=string` |
| `--environment-name` | No | string | -- | Environment for building the platform |
| `--option-settings` | No | list | None | Configuration options for the build environment |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "PlatformSummary": {
        "PlatformArn": "string",
        "PlatformOwner": "string",
        "PlatformStatus": "Creating|Failed|Ready|Deleting|Deleted",
        "PlatformCategory": "string",
        "OperatingSystemName": "string",
        "OperatingSystemVersion": "string",
        "SupportedTierList": ["string"],
        "SupportedAddonList": ["string"],
        "PlatformLifecycleState": "string",
        "PlatformVersion": "string",
        "PlatformBranchName": "string",
        "PlatformBranchLifecycleState": "string"
    },
    "Builder": {
        "ARN": "string"
    }
}
```

---

### 6.2 `describe-platform-version`

Describes a platform version.

**Synopsis:**
```bash
aws elasticbeanstalk describe-platform-version \
    [--platform-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--platform-arn` | No | string | -- | ARN of the platform version |

**Output Schema:**
```json
{
    "PlatformDescription": {
        "PlatformArn": "string",
        "PlatformOwner": "string",
        "PlatformName": "string",
        "PlatformVersion": "string",
        "SolutionStackName": "string",
        "PlatformStatus": "Creating|Failed|Ready|Deleting|Deleted",
        "DateCreated": "timestamp",
        "DateUpdated": "timestamp",
        "PlatformCategory": "string",
        "Description": "string",
        "Maintainer": "string",
        "OperatingSystemName": "string",
        "OperatingSystemVersion": "string",
        "ProgrammingLanguages": [
            {
                "Name": "string",
                "Version": "string"
            }
        ],
        "Frameworks": [
            {
                "Name": "string",
                "Version": "string"
            }
        ],
        "CustomAmiList": [
            {
                "VirtualizationType": "string",
                "ImageId": "string"
            }
        ],
        "SupportedTierList": ["string"],
        "SupportedAddonList": ["string"],
        "PlatformLifecycleState": "string",
        "PlatformBranchName": "string",
        "PlatformBranchLifecycleState": "string"
    }
}
```

---

### 6.3 `list-platform-versions`

Lists the platform versions available for your account. **Paginated operation.**

**Synopsis:**
```bash
aws elasticbeanstalk list-platform-versions \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `Type=string,Operator=string,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Types:**
- `PlatformName` - Filter by platform name
- `PlatformOwner` - Filter by owner (`self`, `amazon`)
- `PlatformStatus` - Filter by status

**Output Schema:**
```json
{
    "PlatformSummaryList": [
        {
            "PlatformArn": "string",
            "PlatformOwner": "string",
            "PlatformStatus": "Creating|Failed|Ready|Deleting|Deleted",
            "PlatformCategory": "string",
            "OperatingSystemName": "string",
            "OperatingSystemVersion": "string",
            "SupportedTierList": ["string"],
            "SupportedAddonList": ["string"],
            "PlatformLifecycleState": "string",
            "PlatformVersion": "string",
            "PlatformBranchName": "string",
            "PlatformBranchLifecycleState": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `list-platform-branches`

Lists the platform branches available for your account. **Paginated operation.**

**Synopsis:**
```bash
aws elasticbeanstalk list-platform-branches \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters. Shorthand: `Attribute=string,Operator=string,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Attributes:**
- `BranchName` - Branch name
- `LifecycleState` - Lifecycle state (`beta`, `supported`, `deprecated`, `retired`)
- `PlatformName` - Platform name
- `TierType` - Tier type (`WebServer/Standard`, `Worker/SQS/HTTP`)

**Output Schema:**
```json
{
    "PlatformBranchSummaryList": [
        {
            "PlatformName": "string",
            "BranchName": "string",
            "LifecycleState": "string",
            "BranchOrder": "integer",
            "SupportedTierList": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `delete-platform-version`

Deletes the specified version of a custom platform.

**Synopsis:**
```bash
aws elasticbeanstalk delete-platform-version \
    [--platform-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--platform-arn` | No | string | -- | ARN of the platform version to delete |

**Output Schema:**
```json
{
    "PlatformSummary": {
        "PlatformArn": "string",
        "PlatformOwner": "string",
        "PlatformStatus": "Creating|Failed|Ready|Deleting|Deleted",
        "PlatformCategory": "string",
        "OperatingSystemName": "string",
        "OperatingSystemVersion": "string"
    }
}
```
