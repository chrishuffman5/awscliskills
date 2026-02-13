# Configuration

### 5.1 `create-configuration-template`

Creates an Elastic Beanstalk configuration template from an existing environment, solution stack, or another template.

**Synopsis:**
```bash
aws elasticbeanstalk create-configuration-template \
    --application-name <value> \
    --template-name <value> \
    [--solution-stack-name <value>] \
    [--platform-arn <value>] \
    [--source-configuration <value>] \
    [--environment-id <value>] \
    [--description <value>] \
    [--option-settings <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--template-name` | **Yes** | string | -- | Name of the configuration template |
| `--solution-stack-name` | No | string | -- | Solution stack for the template |
| `--platform-arn` | No | string | -- | Platform ARN |
| `--source-configuration` | No | structure | None | Source from another template. Shorthand: `ApplicationName=string,TemplateName=string` |
| `--environment-id` | No | string | -- | Create from an existing environment |
| `--description` | No | string | -- | Description |
| `--option-settings` | No | list | None | Configuration options |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "SolutionStackName": "string",
    "PlatformArn": "string",
    "ApplicationName": "string",
    "TemplateName": "string",
    "Description": "string",
    "EnvironmentName": "string",
    "DeploymentStatus": "deployed|pending|failed",
    "DateCreated": "timestamp",
    "DateUpdated": "timestamp",
    "OptionSettings": [
        {
            "ResourceName": "string",
            "Namespace": "string",
            "OptionName": "string",
            "Value": "string"
        }
    ]
}
```

---

### 5.2 `describe-configuration-settings`

Returns a description of the settings for the specified configuration set (either a saved template or the running environment).

**Synopsis:**
```bash
aws elasticbeanstalk describe-configuration-settings \
    --application-name <value> \
    [--template-name <value>] \
    [--environment-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--template-name` | No | string | -- | Configuration template name |
| `--environment-name` | No | string | -- | Environment name |

**Output Schema:**
```json
{
    "ConfigurationSettings": [
        {
            "SolutionStackName": "string",
            "PlatformArn": "string",
            "ApplicationName": "string",
            "TemplateName": "string",
            "Description": "string",
            "EnvironmentName": "string",
            "DeploymentStatus": "deployed|pending|failed",
            "DateCreated": "timestamp",
            "DateUpdated": "timestamp",
            "OptionSettings": [
                {
                    "ResourceName": "string",
                    "Namespace": "string",
                    "OptionName": "string",
                    "Value": "string"
                }
            ]
        }
    ]
}
```

---

### 5.3 `update-configuration-template`

Updates the specified configuration template.

**Synopsis:**
```bash
aws elasticbeanstalk update-configuration-template \
    --application-name <value> \
    --template-name <value> \
    [--description <value>] \
    [--option-settings <value>] \
    [--options-to-remove <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--template-name` | **Yes** | string | -- | Template name |
| `--description` | No | string | -- | Updated description |
| `--option-settings` | No | list | None | Configuration options to set |
| `--options-to-remove` | No | list | None | Configuration options to remove |

**Output Schema:**
Same as `create-configuration-template`.

---

### 5.4 `delete-configuration-template`

Deletes the specified configuration template.

**Synopsis:**
```bash
aws elasticbeanstalk delete-configuration-template \
    --application-name <value> \
    --template-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--template-name` | **Yes** | string | -- | Template name to delete |

**Output Schema:**
```json
{}
```

---

### 5.5 `describe-configuration-options`

Describes the configuration options that are used in a specified configuration template or environment.

**Synopsis:**
```bash
aws elasticbeanstalk describe-configuration-options \
    [--application-name <value>] \
    [--template-name <value>] \
    [--environment-name <value>] \
    [--solution-stack-name <value>] \
    [--platform-arn <value>] \
    [--options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | No | string | -- | Application name |
| `--template-name` | No | string | -- | Template name |
| `--environment-name` | No | string | -- | Environment name |
| `--solution-stack-name` | No | string | -- | Solution stack name |
| `--platform-arn` | No | string | -- | Platform ARN |
| `--options` | No | list | None | Specific options to describe. Shorthand: `ResourceName=string,Namespace=string,OptionName=string ...` |

**Output Schema:**
```json
{
    "SolutionStackName": "string",
    "PlatformArn": "string",
    "Options": [
        {
            "Namespace": "string",
            "Name": "string",
            "DefaultValue": "string",
            "ChangeSeverity": "string",
            "UserDefined": "boolean",
            "ValueType": "Scalar|List",
            "ValueOptions": ["string"],
            "MinValue": "integer",
            "MaxValue": "integer",
            "MaxLength": "integer",
            "Regex": {
                "Pattern": "string",
                "Label": "string"
            }
        }
    ]
}
```

---

### 5.6 `validate-configuration-settings`

Validates the specified configuration settings against a solution stack or template.

**Synopsis:**
```bash
aws elasticbeanstalk validate-configuration-settings \
    --application-name <value> \
    --option-settings <value> \
    [--template-name <value>] \
    [--environment-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--option-settings` | **Yes** | list | -- | Configuration options to validate |
| `--template-name` | No | string | -- | Template to validate against |
| `--environment-name` | No | string | -- | Environment to validate against |

**Output Schema:**
```json
{
    "Messages": [
        {
            "Message": "string",
            "Severity": "error|warning",
            "Namespace": "string",
            "OptionName": "string"
        }
    ]
}
```
