# Applications

### 1.1 `create-application`

Creates an application that has one configuration template named `default` and no application versions.

**Synopsis:**
```bash
aws elasticbeanstalk create-application \
    --application-name <value> \
    [--description <value>] \
    [--resource-lifecycle-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application (1-100 chars) |
| `--description` | No | string | -- | Description of the application (max 200 chars) |
| `--resource-lifecycle-config` | No | structure | None | Lifecycle settings for application versions |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Resource Lifecycle Config Structure:**
```json
{
    "ServiceRole": "string",
    "VersionLifecycleConfig": {
        "MaxCountRule": {
            "Enabled": "boolean",
            "MaxCount": "integer",
            "DeleteSourceFromS3": "boolean"
        },
        "MaxAgeRule": {
            "Enabled": "boolean",
            "MaxAgeInDays": "integer",
            "DeleteSourceFromS3": "boolean"
        }
    }
}
```

**Output Schema:**
```json
{
    "Application": {
        "ApplicationArn": "string",
        "ApplicationName": "string",
        "Description": "string",
        "DateCreated": "timestamp",
        "DateUpdated": "timestamp",
        "Versions": ["string"],
        "ConfigurationTemplates": ["string"],
        "ResourceLifecycleConfig": {
            "ServiceRole": "string",
            "VersionLifecycleConfig": {
                "MaxCountRule": {},
                "MaxAgeRule": {}
            }
        }
    }
}
```

---

### 1.2 `describe-applications`

Returns the descriptions of existing applications.

**Synopsis:**
```bash
aws elasticbeanstalk describe-applications \
    [--application-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-names` | No | list(string) | None | List of application names to describe |

**Output Schema:**
```json
{
    "Applications": [
        {
            "ApplicationArn": "string",
            "ApplicationName": "string",
            "Description": "string",
            "DateCreated": "timestamp",
            "DateUpdated": "timestamp",
            "Versions": ["string"],
            "ConfigurationTemplates": ["string"],
            "ResourceLifecycleConfig": {}
        }
    ]
}
```

---

### 1.3 `update-application`

Updates the specified application to have the specified properties.

**Synopsis:**
```bash
aws elasticbeanstalk update-application \
    --application-name <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application to update |
| `--description` | No | string | -- | Updated description |

**Output Schema:**
```json
{
    "Application": {
        "ApplicationArn": "string",
        "ApplicationName": "string",
        "Description": "string",
        "DateCreated": "timestamp",
        "DateUpdated": "timestamp",
        "Versions": ["string"],
        "ConfigurationTemplates": ["string"],
        "ResourceLifecycleConfig": {}
    }
}
```

---

### 1.4 `delete-application`

Deletes the specified application along with all associated versions and configurations. You cannot delete an application that has a running environment.

**Synopsis:**
```bash
aws elasticbeanstalk delete-application \
    --application-name <value> \
    [--terminate-env-by-force | --no-terminate-env-by-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application to delete |
| `--terminate-env-by-force` | No | boolean | false | Force terminate running environments before deleting |

**Output Schema:**
```json
{}
```
