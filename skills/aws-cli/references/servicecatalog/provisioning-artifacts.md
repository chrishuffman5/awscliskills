# Provisioning Artifacts

### 3.1 `create-provisioning-artifact`

Creates a provisioning artifact (version) for the specified product.

**Synopsis:**
```bash
aws servicecatalog create-provisioning-artifact \
    --product-id <value> \
    --parameters <value> \
    --idempotency-token <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-id` | **Yes** | string | -- | Product identifier |
| `--parameters` | **Yes** | structure | -- | Provisioning artifact configuration |
| `--idempotency-token` | **Yes** | string | -- | Idempotency token |
| `--accept-language` | No | string | None | Language code |

**Parameters Structure:**
```json
{
    "Name": "string",
    "Description": "string",
    "Info": {
        "LoadTemplateFromURL": "string"
    },
    "Type": "CLOUD_FORMATION_TEMPLATE|MARKETPLACE_AMI|MARKETPLACE_CAR|TERRAFORM_OPEN_SOURCE|TERRAFORM_CLOUD|EXTERNAL",
    "DisableTemplateValidation": true|false
}
```

**Output Schema:**
```json
{
    "ProvisioningArtifactDetail": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "Type": "string",
        "CreatedTime": "timestamp",
        "Active": "boolean",
        "Guidance": "DEFAULT|DEPRECATED",
        "SourceRevision": "string"
    },
    "Info": {
        "string": "string"
    },
    "Status": "AVAILABLE|CREATING|FAILED"
}
```

---

### 3.2 `delete-provisioning-artifact`

Deletes the specified provisioning artifact. Cannot delete an artifact that is associated with a product that has been shared or has provisioned products.

**Synopsis:**
```bash
aws servicecatalog delete-provisioning-artifact \
    --product-id <value> \
    --provisioning-artifact-id <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-id` | **Yes** | string | -- | Product identifier |
| `--provisioning-artifact-id` | **Yes** | string | -- | Provisioning artifact identifier |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{}
```

---

### 3.3 `describe-provisioning-artifact`

Gets information about the specified provisioning artifact.

**Synopsis:**
```bash
aws servicecatalog describe-provisioning-artifact \
    [--provisioning-artifact-id <value>] \
    [--product-id <value>] \
    [--provisioning-artifact-name <value>] \
    [--product-name <value>] \
    [--verbose | --no-verbose] \
    [--include-provisioning-artifact-parameters | --no-include-provisioning-artifact-parameters] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provisioning-artifact-id` | No | string | None | Artifact identifier |
| `--product-id` | No | string | None | Product identifier |
| `--provisioning-artifact-name` | No | string | None | Artifact name |
| `--product-name` | No | string | None | Product name |
| `--verbose` | No | boolean | false | Include additional CloudFormation template details |
| `--include-provisioning-artifact-parameters` | No | boolean | false | Include provisioning parameters |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ProvisioningArtifactDetail": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "Type": "string",
        "CreatedTime": "timestamp",
        "Active": "boolean",
        "Guidance": "DEFAULT|DEPRECATED",
        "SourceRevision": "string"
    },
    "Info": {
        "string": "string"
    },
    "Status": "AVAILABLE|CREATING|FAILED",
    "ProvisioningArtifactParameters": [
        {
            "ParameterKey": "string",
            "DefaultValue": "string",
            "ParameterType": "string",
            "IsNoEcho": "boolean",
            "Description": "string",
            "ParameterConstraints": {
                "AllowedValues": ["string"],
                "AllowedPattern": "string",
                "ConstraintDescription": "string",
                "MaxLength": "string",
                "MinLength": "string",
                "MaxValue": "string",
                "MinValue": "string"
            }
        }
    ]
}
```

---

### 3.4 `update-provisioning-artifact`

Updates the specified provisioning artifact properties.

**Synopsis:**
```bash
aws servicecatalog update-provisioning-artifact \
    --product-id <value> \
    --provisioning-artifact-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--active | --no-active] \
    [--guidance <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-id` | **Yes** | string | -- | Product identifier |
| `--provisioning-artifact-id` | **Yes** | string | -- | Artifact identifier |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--active` | No | boolean | None | Whether the artifact is active |
| `--guidance` | No | string | None | `DEFAULT` or `DEPRECATED` |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ProvisioningArtifactDetail": {
        "Id": "string",
        "Name": "string",
        "Description": "string",
        "Type": "string",
        "CreatedTime": "timestamp",
        "Active": "boolean",
        "Guidance": "DEFAULT|DEPRECATED",
        "SourceRevision": "string"
    },
    "Info": {
        "string": "string"
    },
    "Status": "AVAILABLE|CREATING|FAILED"
}
```

---

### 3.5 `list-provisioning-artifacts`

Lists all provisioning artifacts for the specified product.

**Synopsis:**
```bash
aws servicecatalog list-provisioning-artifacts \
    --product-id <value> \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-id` | **Yes** | string | -- | Product identifier |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ProvisioningArtifactDetails": [
        {
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "Type": "string",
            "CreatedTime": "timestamp",
            "Active": "boolean",
            "Guidance": "DEFAULT|DEPRECATED",
            "SourceRevision": "string"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 3.6 `describe-provisioning-parameters`

Gets information about the configuration required to provision the specified product.

**Synopsis:**
```bash
aws servicecatalog describe-provisioning-parameters \
    [--product-id <value>] \
    [--product-name <value>] \
    [--provisioning-artifact-id <value>] \
    [--provisioning-artifact-name <value>] \
    [--path-id <value>] \
    [--path-name <value>] \
    [--accept-language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-id` | No | string | None | Product identifier |
| `--product-name` | No | string | None | Product name |
| `--provisioning-artifact-id` | No | string | None | Artifact identifier |
| `--provisioning-artifact-name` | No | string | None | Artifact name |
| `--path-id` | No | string | None | Launch path identifier |
| `--path-name` | No | string | None | Launch path name |
| `--accept-language` | No | string | None | Language code |

**Output Schema:**
```json
{
    "ProvisioningArtifactParameters": [
        {
            "ParameterKey": "string",
            "DefaultValue": "string",
            "ParameterType": "string",
            "IsNoEcho": "boolean",
            "Description": "string",
            "ParameterConstraints": {
                "AllowedValues": ["string"],
                "AllowedPattern": "string",
                "ConstraintDescription": "string",
                "MaxLength": "string",
                "MinLength": "string",
                "MaxValue": "string",
                "MinValue": "string"
            }
        }
    ],
    "ConstraintSummaries": [
        {
            "Type": "string",
            "Description": "string"
        }
    ],
    "UsageInstructions": [
        {
            "Type": "string",
            "Value": "string"
        }
    ],
    "TagOptions": [
        {
            "Key": "string",
            "Values": ["string"]
        }
    ],
    "ProvisioningArtifactPreferences": {
        "StackSetAccounts": ["string"],
        "StackSetRegions": ["string"]
    },
    "ProvisioningArtifactOutputs": [
        {
            "Key": "string",
            "Description": "string"
        }
    ],
    "ProvisioningArtifactOutputKeys": [
        {
            "Key": "string",
            "Description": "string"
        }
    ]
}
```
