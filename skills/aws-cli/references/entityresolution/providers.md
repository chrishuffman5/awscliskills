# Providers

### 5.1 `get-provider-service`

Gets details of a third-party provider service used for entity resolution.

**Synopsis:**
```bash
aws entityresolution get-provider-service \
    --provider-name <value> \
    --provider-service-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provider-name` | **Yes** | string | -- | Provider name (1-255 chars) |
| `--provider-service-name` | **Yes** | string | -- | Provider service ARN |

**Output Schema:**
```json
{
    "providerName": "string",
    "providerServiceName": "string",
    "providerServiceDisplayName": "string",
    "providerServiceType": "ASSIGNMENT|ID_MAPPING",
    "providerServiceArn": "string",
    "providerConfigurationDefinition": {},
    "providerIdNameSpaceConfiguration": {
        "description": "string",
        "providerTargetConfigurationDefinition": {},
        "providerSourceConfigurationDefinition": {}
    },
    "providerJobConfiguration": {},
    "providerEndpointConfiguration": {
        "marketplaceConfiguration": {
            "dataSetId": "string",
            "revisionId": "string",
            "assetId": "string",
            "listingId": "string"
        }
    },
    "anonymizedOutput": "boolean",
    "providerEntityOutputDefinition": {},
    "providerIntermediateDataAccessConfiguration": {
        "awsAccountIds": ["string"],
        "requiredBucketActions": ["string"]
    },
    "providerComponentSchema": {
        "schemas": [["string"]],
        "providerSchemaAttributes": [
            {
                "fieldName": "string",
                "type": "string",
                "subType": "string",
                "hashing": "boolean"
            }
        ]
    }
}
```

---

### 5.2 `list-provider-services`

Lists available third-party provider services. **Paginated operation.**

**Synopsis:**
```bash
aws entityresolution list-provider-services \
    [--provider-name <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provider-name` | No | string | None | Filter by provider name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-25) |

**Output Schema:**
```json
{
    "providerServiceSummaries": [
        {
            "providerName": "string",
            "providerServiceName": "string",
            "providerServiceDisplayName": "string",
            "providerServiceType": "ASSIGNMENT|ID_MAPPING",
            "providerServiceArn": "string"
        }
    ],
    "nextToken": "string"
}
```
