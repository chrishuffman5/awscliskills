# Data Stores

### 1.1 `create-fhir-datastore`

Creates a FHIR R4 data store.

**Synopsis:**
```bash
aws healthlake create-fhir-datastore \
    --datastore-type-version <value> \
    [--datastore-name <value>] \
    [--sse-configuration <value>] \
    [--preload-data-config <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--identity-provider-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-type-version` | **Yes** | string | -- | FHIR version. Must be `R4` |
| `--datastore-name` | No | string | None | Data store name (1-256 chars) |
| `--sse-configuration` | No | structure | None | SSE config: `KmsEncryptionConfig={CmkType=string,KmsKeyId=string}` |
| `--preload-data-config` | No | structure | None | Preload data: `PreloadDataType=SYNTHEA` |
| `--client-token` | No | string | None | Idempotency token (1-64 chars) |
| `--tags` | No | list | None | Tags: `Key=string,Value=string ...` (max 200) |
| `--identity-provider-configuration` | No | structure | None | SMART on FHIR config (see below) |

**Identity Provider Configuration Structure:**
```
AuthorizationStrategy=SMART_ON_FHIR_V1|AWS_AUTH,
FineGrainedAuthorizationEnabled=boolean,
Metadata=string,
IdpLambdaArn=string
```

**SSE KmsEncryptionConfig CmkType Values:**
- `CUSTOMER_MANAGED_KMS_KEY` — Use your own KMS key (requires `KmsKeyId`)
- `AWS_OWNED_KMS_KEY` — Use AWS-owned key (default)

**Output Schema:**
```json
{
    "DatastoreId": "string",
    "DatastoreArn": "string",
    "DatastoreStatus": "CREATING",
    "DatastoreEndpoint": "string"
}
```

---

### 1.2 `describe-fhir-datastore`

Gets properties of a FHIR data store.

**Synopsis:**
```bash
aws healthlake describe-fhir-datastore \
    --datastore-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-id` | **Yes** | string | -- | Data store ID (1-32 chars) |

**Output Schema:**
```json
{
    "DatastoreProperties": {
        "DatastoreId": "string",
        "DatastoreArn": "string",
        "DatastoreName": "string",
        "DatastoreStatus": "CREATING|ACTIVE|DELETING|DELETED|CREATE_FAILED",
        "CreatedAt": "timestamp",
        "DatastoreTypeVersion": "R4",
        "DatastoreEndpoint": "string",
        "SseConfiguration": {
            "KmsEncryptionConfig": {
                "CmkType": "CUSTOMER_MANAGED_KMS_KEY|AWS_OWNED_KMS_KEY",
                "KmsKeyId": "string"
            }
        },
        "PreloadDataConfig": {
            "PreloadDataType": "SYNTHEA"
        },
        "IdentityProviderConfiguration": {
            "AuthorizationStrategy": "SMART_ON_FHIR_V1|AWS_AUTH",
            "FineGrainedAuthorizationEnabled": "boolean",
            "Metadata": "string",
            "IdpLambdaArn": "string"
        },
        "ErrorCause": {
            "ErrorMessage": "string",
            "ErrorCategory": "RETRYABLE_ERROR|NON_RETRYABLE_ERROR"
        }
    }
}
```

---

### 1.3 `list-fhir-datastores`

Lists FHIR data stores with optional filters.

**Synopsis:**
```bash
aws healthlake list-fhir-datastores \
    [--filter <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | None | Filter: `DatastoreNameFilter=string,DatastoreStatusFilter=string,CreatedBefore=timestamp,CreatedAfter=timestamp` |
| `--next-token` | No | string | None | Pagination token (max 8192 chars) |
| `--max-results` | No | integer | None | Max results (1-500) |

**Filter DatastoreStatusFilter Values:** `CREATING`, `ACTIVE`, `DELETING`, `DELETED`, `CREATE_FAILED`

**Output Schema:**
```json
{
    "DatastorePropertiesList": [
        {
            "DatastoreId": "string",
            "DatastoreArn": "string",
            "DatastoreName": "string",
            "DatastoreStatus": "string",
            "CreatedAt": "timestamp",
            "DatastoreTypeVersion": "R4",
            "DatastoreEndpoint": "string",
            "SseConfiguration": {},
            "PreloadDataConfig": {},
            "IdentityProviderConfiguration": {},
            "ErrorCause": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `delete-fhir-datastore`

Deletes a FHIR data store and all its contents.

**Synopsis:**
```bash
aws healthlake delete-fhir-datastore \
    --datastore-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-id` | **Yes** | string | -- | Data store ID (1-32 chars) |

**Output Schema:**
```json
{
    "DatastoreId": "string",
    "DatastoreArn": "string",
    "DatastoreStatus": "DELETING",
    "DatastoreEndpoint": "string"
}
```
