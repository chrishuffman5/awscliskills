# Type Registry

### 8.1 `register-type`

Registers an extension (resource type, module, or hook) in the CloudFormation registry.

**Synopsis:**
```bash
aws cloudformation register-type \
    --type-name <value> \
    --schema-handler-package <value> \
    [--type <value>] \
    [--logging-config <value>] \
    [--execution-role-arn <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type-name` | **Yes** | string | -- | Type name (e.g., `MyOrg::MyService::MyResource`) |
| `--schema-handler-package` | **Yes** | string | -- | S3 URL of the handler package ZIP |
| `--type` | No | string | `RESOURCE` | `RESOURCE`, `MODULE`, or `HOOK` |
| `--logging-config` | No | structure | None | Logging configuration. Shorthand: `LogRoleArn=string,LogGroupName=string` |
| `--execution-role-arn` | No | string | None | IAM role ARN for CloudFormation to assume |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "RegistrationToken": "string"
}
```

---

### 8.2 `deregister-type`

Removes a type or type version from the CloudFormation registry.

**Synopsis:**
```bash
aws cloudformation deregister-type \
    [--arn <value>] \
    [--type <value>] \
    [--type-name <value>] \
    [--version-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | No | string | None | ARN of the type version to deregister |
| `--type` | No | string | None | `RESOURCE`, `MODULE`, or `HOOK` |
| `--type-name` | No | string | None | Type name |
| `--version-id` | No | string | None | Version ID to deregister |

**Output:** No output on success (empty JSON `{}`).

---

### 8.3 `describe-type`

Returns detailed information about a registered type.

**Synopsis:**
```bash
aws cloudformation describe-type \
    [--type <value>] \
    [--type-name <value>] \
    [--arn <value>] \
    [--version-id <value>] \
    [--publisher-id <value>] \
    [--public-version-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | No | string | None | `RESOURCE`, `MODULE`, or `HOOK` |
| `--type-name` | No | string | None | Type name |
| `--arn` | No | string | None | Type ARN |
| `--version-id` | No | string | None | Version ID |
| `--publisher-id` | No | string | None | Publisher ID |
| `--public-version-number` | No | string | None | Public version number |

**Output Schema:**
```json
{
    "Arn": "string",
    "Type": "RESOURCE|MODULE|HOOK",
    "TypeName": "string",
    "DefaultVersionId": "string",
    "IsDefaultVersion": true|false,
    "TypeTestsStatus": "PASSED|FAILED|WARNING|NOT_TESTED",
    "TypeTestsStatusDescription": "string",
    "Description": "string",
    "Schema": "string",
    "ProvisioningType": "NON_PROVISIONABLE|IMMUTABLE|FULLY_MUTABLE",
    "DeprecatedStatus": "LIVE|DEPRECATED",
    "LoggingConfig": {
        "LogRoleArn": "string",
        "LogGroupName": "string"
    },
    "RequiredActivatedTypes": [
        {
            "TypeNameAlias": "string",
            "OriginalTypeName": "string",
            "PublisherId": "string",
            "SupportedMajorVersions": ["integer"]
        }
    ],
    "ExecutionRoleArn": "string",
    "Visibility": "PUBLIC|PRIVATE",
    "SourceUrl": "string",
    "DocumentationUrl": "string",
    "LastUpdated": "timestamp",
    "TimeCreated": "timestamp",
    "ConfigurationSchema": "string",
    "PublisherId": "string",
    "OriginalTypeName": "string",
    "OriginalTypeArn": "string",
    "PublicVersionNumber": "string",
    "LatestPublicVersion": "string",
    "IsActivated": true|false,
    "AutoUpdate": true|false
}
```

---

### 8.4 `describe-type-registration`

Returns information about the status of a type registration request.

**Synopsis:**
```bash
aws cloudformation describe-type-registration \
    --registration-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-token` | **Yes** | string | -- | Registration token from `register-type` |

**Output Schema:**
```json
{
    "ProgressStatus": "COMPLETE|IN_PROGRESS|FAILED",
    "Description": "string",
    "TypeArn": "string",
    "TypeVersionArn": "string"
}
```

---

### 8.5 `list-types`

Returns summary information about registered types. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-types \
    [--visibility <value>] \
    [--provisioning-type <value>] \
    [--deprecated-status <value>] \
    [--type <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--visibility` | No | string | `PRIVATE` | `PUBLIC`, `PRIVATE` |
| `--provisioning-type` | No | string | None | `NON_PROVISIONABLE`, `IMMUTABLE`, `FULLY_MUTABLE` |
| `--deprecated-status` | No | string | `LIVE` | `LIVE` or `DEPRECATED` |
| `--type` | No | string | None | `RESOURCE`, `MODULE`, or `HOOK` |
| `--filters` | No | structure | None | Filter criteria. Shorthand: `Category=REGISTERED\|ACTIVATED\|THIRD_PARTY\|AWS_TYPES,PublisherId=string,TypeNamePrefix=string` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "TypeSummaries": [
        {
            "Type": "RESOURCE|MODULE|HOOK",
            "TypeName": "string",
            "DefaultVersionId": "string",
            "TypeArn": "string",
            "LastUpdated": "timestamp",
            "Description": "string",
            "PublisherId": "string",
            "OriginalTypeName": "string",
            "PublicVersionNumber": "string",
            "LatestPublicVersion": "string",
            "PublisherIdentity": "AWS_Marketplace|GitHub|Bitbucket",
            "PublisherName": "string",
            "IsActivated": true|false
        }
    ],
    "NextToken": "string"
}
```

---

### 8.6 `list-type-registrations`

Returns a list of registration tokens for specified type registration requests. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-type-registrations \
    [--type <value>] \
    [--type-name <value>] \
    [--type-arn <value>] \
    [--registration-status-filter <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | No | string | None | `RESOURCE`, `MODULE`, or `HOOK` |
| `--type-name` | No | string | None | Type name |
| `--type-arn` | No | string | None | Type ARN |
| `--registration-status-filter` | No | string | None | `COMPLETE`, `IN_PROGRESS`, `FAILED` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "RegistrationTokenList": ["string"],
    "NextToken": "string"
}
```

---

### 8.7 `list-type-versions`

Returns summary information about versions of a type. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-type-versions \
    [--type <value>] \
    [--type-name <value>] \
    [--arn <value>] \
    [--deprecated-status <value>] \
    [--publisher-id <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | No | string | None | `RESOURCE`, `MODULE`, or `HOOK` |
| `--type-name` | No | string | None | Type name |
| `--arn` | No | string | None | Type ARN |
| `--deprecated-status` | No | string | `LIVE` | `LIVE` or `DEPRECATED` |
| `--publisher-id` | No | string | None | Publisher ID |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "TypeVersionSummaries": [
        {
            "Type": "RESOURCE|MODULE|HOOK",
            "TypeName": "string",
            "VersionId": "string",
            "IsDefaultVersion": true|false,
            "Arn": "string",
            "TimeCreated": "timestamp",
            "Description": "string",
            "PublicVersionNumber": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.8 `set-type-default-version`

Specifies the default version of a type. The default version is used in operations where no version is specified.

**Synopsis:**
```bash
aws cloudformation set-type-default-version \
    [--arn <value>] \
    [--type <value>] \
    [--type-name <value>] \
    [--version-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | No | string | None | Type version ARN |
| `--type` | No | string | None | `RESOURCE`, `MODULE`, or `HOOK` |
| `--type-name` | No | string | None | Type name |
| `--version-id` | No | string | None | Version ID to set as default |

**Output:** No output on success (empty JSON `{}`).

---

### 8.9 `set-type-configuration`

Sets the configuration data for a registered type. Used for hooks and third-party resources that require configuration.

**Synopsis:**
```bash
aws cloudformation set-type-configuration \
    --configuration <value> \
    [--type-arn <value>] \
    [--type <value>] \
    [--type-name <value>] \
    [--configuration-alias <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration` | **Yes** | string | -- | Configuration JSON conforming to the type's configuration schema |
| `--type-arn` | No | string | None | Type ARN |
| `--type` | No | string | None | `RESOURCE`, `MODULE`, or `HOOK` |
| `--type-name` | No | string | None | Type name |
| `--configuration-alias` | No | string | `default` | Configuration alias |

**Output Schema:**
```json
{
    "ConfigurationArn": "string"
}
```

---

### 8.10 `batch-describe-type-configurations`

Returns configuration data for the specified types.

**Synopsis:**
```bash
aws cloudformation batch-describe-type-configurations \
    --type-configuration-identifiers <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type-configuration-identifiers` | **Yes** | list | -- | Type identifiers. Shorthand: `TypeArn=string,TypeConfigurationAlias=string,TypeConfigurationArn=string,Type=RESOURCE\|MODULE\|HOOK,TypeName=string ...` |

**Output Schema:**
```json
{
    "Errors": [
        {
            "ErrorCode": "string",
            "ErrorMessage": "string",
            "TypeConfigurationIdentifier": {
                "TypeArn": "string",
                "TypeConfigurationAlias": "string",
                "TypeConfigurationArn": "string",
                "Type": "string",
                "TypeName": "string"
            }
        }
    ],
    "UnprocessedTypeConfigurations": [],
    "TypeConfigurations": [
        {
            "Arn": "string",
            "Alias": "string",
            "Configuration": "string",
            "LastUpdated": "timestamp",
            "TypeArn": "string",
            "TypeName": "string",
            "IsDefaultConfiguration": true|false
        }
    ]
}
```

---

### 8.11 `publish-type`

Publishes the specified registered type to the CloudFormation registry as a public type.

**Synopsis:**
```bash
aws cloudformation publish-type \
    [--type <value>] \
    [--arn <value>] \
    [--type-name <value>] \
    [--public-version-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | No | string | None | `RESOURCE`, `MODULE`, or `HOOK` |
| `--arn` | No | string | None | Type ARN |
| `--type-name` | No | string | None | Type name |
| `--public-version-number` | No | string | None | Public version number (semver format) |

**Output Schema:**
```json
{
    "PublicTypeArn": "string"
}
```

---

### 8.12 `test-type`

Tests a registered type against the CloudFormation contract tests.

**Synopsis:**
```bash
aws cloudformation test-type \
    [--arn <value>] \
    [--type <value>] \
    [--type-name <value>] \
    [--version-id <value>] \
    [--log-delivery-bucket <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | No | string | None | Type ARN |
| `--type` | No | string | None | `RESOURCE`, `MODULE`, or `HOOK` |
| `--type-name` | No | string | None | Type name |
| `--version-id` | No | string | None | Version ID |
| `--log-delivery-bucket` | No | string | None | S3 bucket for test logs |

**Output Schema:**
```json
{
    "TypeVersionArn": "string"
}
```

---

### 8.13 `activate-type`

Activates a public third-party type for use in your account. Once activated, you can use the type in CloudFormation operations.

**Synopsis:**
```bash
aws cloudformation activate-type \
    [--type <value>] \
    [--public-type-arn <value>] \
    [--publisher-id <value>] \
    [--type-name <value>] \
    [--type-name-alias <value>] \
    [--auto-update | --no-auto-update] \
    [--logging-config <value>] \
    [--execution-role-arn <value>] \
    [--version-bump <value>] \
    [--major-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | No | string | None | `RESOURCE`, `MODULE`, or `HOOK` |
| `--public-type-arn` | No | string | None | ARN of the public type |
| `--publisher-id` | No | string | None | Publisher ID |
| `--type-name` | No | string | None | Type name |
| `--type-name-alias` | No | string | None | Alias for the type in your account |
| `--auto-update` | No | boolean | false | Automatically update when new version is published |
| `--logging-config` | No | structure | None | Logging config |
| `--execution-role-arn` | No | string | None | Execution role ARN |
| `--version-bump` | No | string | None | `MAJOR` or `MINOR` |
| `--major-version` | No | long | None | Major version to activate |

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

### 8.14 `deactivate-type`

Deactivates a type that was previously activated in your account.

**Synopsis:**
```bash
aws cloudformation deactivate-type \
    [--type-name <value>] \
    [--type <value>] \
    [--arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type-name` | No | string | None | Type name |
| `--type` | No | string | None | `RESOURCE`, `MODULE`, or `HOOK` |
| `--arn` | No | string | None | Type ARN |

**Output:** No output on success (empty JSON `{}`).

---

### 8.15 `register-publisher`

Registers your account as a publisher of public extensions in the CloudFormation registry.

**Synopsis:**
```bash
aws cloudformation register-publisher \
    [--accept-terms-and-conditions | --no-accept-terms-and-conditions] \
    [--connection-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--accept-terms-and-conditions` | No | boolean | false | Accept the terms and conditions for publishing |
| `--connection-arn` | No | string | None | ARN of the CodeStar connection for identity verification |

**Output Schema:**
```json
{
    "PublisherId": "string"
}
```

---

### 8.16 `describe-publisher`

Returns information about a CloudFormation extension publisher.

**Synopsis:**
```bash
aws cloudformation describe-publisher \
    [--publisher-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--publisher-id` | No | string | None | Publisher ID. Omit to describe the calling account |

**Output Schema:**
```json
{
    "PublisherId": "string",
    "PublisherStatus": "VERIFIED|UNVERIFIED",
    "IdentityProvider": "AWS_Marketplace|GitHub|Bitbucket",
    "PublisherProfile": "string"
}
```

---

### 8.17 `record-handler-progress`

Reports progress of a resource handler to CloudFormation. Used by resource type developers to report status from their handler code.

**Synopsis:**
```bash
aws cloudformation record-handler-progress \
    --bearer-token <value> \
    --operation-status <value> \
    --current-operation-status <value> \
    [--error-code <value>] \
    [--status-message <value>] \
    [--resource-model <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bearer-token` | **Yes** | string | -- | Bearer token from the handler request |
| `--operation-status` | **Yes** | string | -- | `PENDING`, `IN_PROGRESS`, `SUCCESS`, `FAILED` |
| `--current-operation-status` | **Yes** | string | -- | Current operation status |
| `--error-code` | No | string | None | Error code: `NotUpdatable`, `InvalidRequest`, `AccessDenied`, `InvalidCredentials`, `AlreadyExists`, `NotFound`, `ResourceConflict`, `Throttling`, `ServiceLimitExceeded`, `NotStabilized`, `GeneralServiceException`, `ServiceInternalError`, `NetworkFailure`, `InternalFailure`, `InvalidTypeConfiguration`, `HandlerInternalFailure`, `NonCompliant`, `Unknown`, `UnsupportedTarget` |
| `--status-message` | No | string | None | Status message |
| `--resource-model` | No | string | None | JSON resource model |
| `--client-request-token` | No | string | None | Client request token |

**Output:** No output on success (empty JSON `{}`).
