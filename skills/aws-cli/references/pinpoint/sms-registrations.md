# SMS v2 Registrations

All commands in this section use `aws pinpoint-sms-voice-v2`.

## Registrations

### 19.1 `create-registration`

Creates a new registration for regulatory compliance (e.g., 10DLC, toll-free).

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 create-registration \
    --registration-type <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-type` | **Yes** | string | -- | Registration type (use `describe-registration-type-definitions` to list) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "RegistrationArn": "string",
    "RegistrationId": "string",
    "RegistrationType": "string",
    "RegistrationStatus": "CREATED|SUBMITTED|AWS_REVIEWING|REVIEWING|REQUIRES_AUTHENTICATION|PROVISIONING|COMPLETE|REQUIRES_UPDATES|CLOSED|DELETED",
    "CurrentVersionNumber": "long",
    "AdditionalAttributes": {"string": "string"},
    "Tags": [{"Key": "string", "Value": "string"}],
    "CreatedTimestamp": "timestamp"
}
```

---

### 19.2 `describe-registrations`

Describes registrations in your account.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-registrations \
    [--registration-ids <value>] \
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
| `--registration-ids` | No | list | None | Registration IDs or ARNs (max 5) |
| `--filters` | No | list | None | Filters: `registration-type`, `registration-status` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Registrations": [
        {
            "RegistrationArn": "string",
            "RegistrationId": "string",
            "RegistrationType": "string",
            "RegistrationStatus": "string",
            "CurrentVersionNumber": "long",
            "ApprovedVersionNumber": "long",
            "LatestDeniedVersionNumber": "long",
            "AdditionalAttributes": {"string": "string"},
            "CreatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 19.3 `delete-registration`

Deletes a registration.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-registration \
    --registration-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-id` | **Yes** | string | -- | Registration ID or ARN |

**Output Schema:** Same as single entry from `describe-registrations`.

---

### 19.4 `submit-registration-version`

Submits a registration version for review and approval.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 submit-registration-version \
    --registration-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-id` | **Yes** | string | -- | Registration ID or ARN |

**Output Schema:**
```json
{
    "RegistrationArn": "string",
    "RegistrationId": "string",
    "VersionNumber": "long",
    "RegistrationVersionStatus": "DRAFT|SUBMITTED|AWS_REVIEWING|REVIEWING|REQUIRES_AUTHENTICATION|APPROVED|DISCARDED|DENIED|REVOKED|ARCHIVED",
    "RegistrationVersionStatusHistory": {
        "DraftTimestamp": "timestamp",
        "SubmittedTimestamp": "timestamp",
        "ApprovedTimestamp": "timestamp",
        "DeniedTimestamp": "timestamp"
    }
}
```

---

### 19.5 `describe-registration-versions`

Describes versions of a registration.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-registration-versions \
    --registration-id <value> \
    [--version-numbers <value>] \
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
| `--registration-id` | **Yes** | string | -- | Registration ID or ARN |
| `--version-numbers` | No | list | None | Version numbers to describe (max 5) |
| `--filters` | No | list | None | Filter: `registration-version-status` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RegistrationArn": "string",
    "RegistrationId": "string",
    "RegistrationVersions": [
        {
            "VersionNumber": "long",
            "RegistrationVersionStatus": "string",
            "RegistrationVersionStatusHistory": {},
            "DeniedReasons": [
                {
                    "Reason": "string",
                    "ShortDescription": "string",
                    "LongDescription": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 19.6 `discard-registration-version`

Discards the current draft version of a registration.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 discard-registration-version \
    --registration-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-id` | **Yes** | string | -- | Registration ID or ARN |

**Output Schema:** Same as `submit-registration-version`.

---

## Registration Fields

### 19.7 `describe-registration-type-definitions`

Lists available registration type definitions.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-registration-type-definitions \
    [--registration-types <value>] \
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
| `--registration-types` | No | list | None | Registration types to describe (max 5) |
| `--filters` | No | list | None | Filters: `supported-association-resource-type`, `supported-association-iso-country-code` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RegistrationTypeDefinitions": [
        {
            "RegistrationType": "string",
            "SupportedAssociations": [
                {
                    "ResourceType": "string",
                    "IsoCountryCode": "string",
                    "AssociationBehavior": "ASSOCIATE_BEFORE_SUBMIT|ASSOCIATE_ON_APPROVAL|ASSOCIATE_AFTER_COMPLETE",
                    "DisassociationBehavior": "string"
                }
            ],
            "DisplayHints": {
                "Title": "string",
                "ShortDescription": "string",
                "LongDescription": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 19.8 `describe-registration-field-definitions`

Describes field definitions for a registration type.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-registration-field-definitions \
    --registration-type <value> \
    [--section-path <value>] \
    [--field-paths <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-type` | **Yes** | string | -- | Registration type |
| `--section-path` | No | string | None | Section path within the form |
| `--field-paths` | No | list | None | Field paths to describe (max 5) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RegistrationType": "string",
    "RegistrationFieldDefinitions": [
        {
            "SectionPath": "string",
            "FieldPath": "string",
            "FieldType": "SELECT|TEXT|ATTACHMENT",
            "FieldRequirement": "REQUIRED|CONDITIONAL|OPTIONAL",
            "SelectValidation": {"MinChoices": "integer", "MaxChoices": "integer", "Options": ["string"]},
            "TextValidation": {"MinLength": "integer", "MaxLength": "integer", "Pattern": "string"},
            "DisplayHints": {"Title": "string", "ShortDescription": "string"}
        }
    ],
    "NextToken": "string"
}
```

---

### 19.9 `put-registration-field-value`

Sets a field value on a registration.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 put-registration-field-value \
    --registration-id <value> \
    --field-path <value> \
    [--select-choices <value>] \
    [--text-value <value>] \
    [--registration-attachment-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-id` | **Yes** | string | -- | Registration ID or ARN |
| `--field-path` | **Yes** | string | -- | Field path from field definitions |
| `--select-choices` | No | list | None | Values for select fields |
| `--text-value` | No | string | None | Value for text fields |
| `--registration-attachment-id` | No | string | None | Attachment ID for file fields |

**Output Schema:**
```json
{
    "RegistrationArn": "string",
    "RegistrationId": "string",
    "VersionNumber": "long",
    "FieldPath": "string",
    "SelectChoices": ["string"],
    "TextValue": "string",
    "RegistrationAttachmentId": "string"
}
```

---

### 19.10 `describe-registration-field-values`

Describes field values for a registration.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-registration-field-values \
    --registration-id <value> \
    [--version-number <value>] \
    [--section-path <value>] \
    [--field-paths <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-id` | **Yes** | string | -- | Registration ID or ARN |
| `--version-number` | No | long | None | Version number to describe |
| `--section-path` | No | string | None | Section path |
| `--field-paths` | No | list | None | Field paths to describe (max 5) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RegistrationArn": "string",
    "RegistrationId": "string",
    "VersionNumber": "long",
    "RegistrationFieldValues": [
        {
            "FieldPath": "string",
            "SelectChoices": ["string"],
            "TextValue": "string",
            "RegistrationAttachmentId": "string",
            "DeniedReason": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## Registration Attachments

### 19.11 `create-registration-attachment`

Uploads a file attachment for use in registrations.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 create-registration-attachment \
    [--attachment-body <value>] \
    [--attachment-url <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-body` | No | blob | None | File content (max 500KB, PDF/JPEG/PNG) |
| `--attachment-url` | No | string | None | S3 URI: `s3://bucket/key` |
| `--tags` | No | list | None | Tags |
| `--client-token` | No | string | Auto | Idempotency token |

Use either `--attachment-body` or `--attachment-url`, not both.

**Output Schema:**
```json
{
    "RegistrationAttachmentArn": "string",
    "RegistrationAttachmentId": "string",
    "AttachmentStatus": "UPLOAD_IN_PROGRESS|UPLOAD_COMPLETE|UPLOAD_FAILED|DELETED",
    "Tags": [{"Key": "string", "Value": "string"}],
    "CreatedTimestamp": "timestamp"
}
```

---

### 19.12 `describe-registration-attachments`

Describes registration attachments.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-registration-attachments \
    [--registration-attachment-ids <value>] \
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
| `--registration-attachment-ids` | No | list | None | Attachment IDs (max 5) |
| `--filters` | No | list | None | Filter: `attachment-status` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RegistrationAttachments": [
        {
            "RegistrationAttachmentArn": "string",
            "RegistrationAttachmentId": "string",
            "AttachmentStatus": "UPLOAD_IN_PROGRESS|UPLOAD_COMPLETE|UPLOAD_FAILED|DELETED",
            "AttachmentUploadErrorReason": "INTERNAL_ERROR",
            "CreatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 19.13 `delete-registration-attachment`

Deletes a registration attachment.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-registration-attachment \
    --registration-attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-attachment-id` | **Yes** | string | -- | Attachment ID or ARN |

**Output Schema:** Same as single entry from `describe-registration-attachments`.

---

## Registration Associations

### 19.14 `create-registration-association`

Associates a registration with an origination identity (phone number or sender ID).

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 create-registration-association \
    --registration-id <value> \
    --resource-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-id` | **Yes** | string | -- | Registration ID or ARN |
| `--resource-id` | **Yes** | string | -- | Origination identity ID (phone number or sender ID) |

**Output Schema:**
```json
{
    "RegistrationArn": "string",
    "RegistrationId": "string",
    "RegistrationType": "string",
    "ResourceArn": "string",
    "ResourceId": "string",
    "ResourceType": "string",
    "IsoCountryCode": "string",
    "PhoneNumber": "string"
}
```

---

### 19.15 `delete-registration-field-value`

Deletes a field value from a registration.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-registration-field-value \
    --registration-id <value> \
    --field-path <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-id` | **Yes** | string | -- | Registration ID or ARN |
| `--field-path` | **Yes** | string | -- | Field path to delete |

**Output Schema:**
```json
{
    "RegistrationArn": "string",
    "RegistrationId": "string",
    "VersionNumber": "long",
    "FieldPath": "string",
    "SelectChoices": ["string"],
    "TextValue": "string",
    "RegistrationAttachmentId": "string"
}
```

---

### 19.16 `describe-registration-section-definitions`

Describes section definitions for a registration type.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-registration-section-definitions \
    --registration-type <value> \
    [--section-paths <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registration-type` | **Yes** | string | -- | Registration type |
| `--section-paths` | No | list | None | Section paths to describe (max 5) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RegistrationType": "string",
    "RegistrationSectionDefinitions": [
        {
            "SectionPath": "string",
            "DisplayHints": {
                "Title": "string",
                "ShortDescription": "string",
                "LongDescription": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 19.17 `list-registration-associations`

Lists associations for a registration.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 list-registration-associations \
    --registration-id <value> \
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
| `--registration-id` | **Yes** | string | -- | Registration ID or ARN |
| `--filters` | No | list | None | Filters: `resource-type`, `iso-country-code` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RegistrationArn": "string",
    "RegistrationId": "string",
    "RegistrationType": "string",
    "RegistrationAssociations": [
        {
            "ResourceArn": "string",
            "ResourceId": "string",
            "ResourceType": "string",
            "IsoCountryCode": "string",
            "PhoneNumber": "string"
        }
    ],
    "NextToken": "string"
}
```
