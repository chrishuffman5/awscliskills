# Entities

### 1.1 `describe-entity`

Returns the metadata and content of an entity from the AWS Marketplace Catalog.

**Synopsis:**
```bash
aws marketplace-catalog describe-entity \
    --catalog <value> \
    --entity-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog` | **Yes** | string | -- | The catalog related to the request. Fixed value: `AWSMarketplace` |
| `--entity-id` | **Yes** | string | -- | The unique ID of the entity to describe (1-255 chars) |

**Output Schema:**
```json
{
    "EntityType": "string",
    "EntityIdentifier": "string",
    "EntityArn": "string",
    "LastModifiedDate": "string",
    "Details": "string",
    "DetailsDocument": {}
}
```

| Field | Description |
|-------|-------------|
| `EntityType` | Named type in format `EntityType@Version` |
| `EntityIdentifier` | Entity identifier in format `EntityId@RevisionId` |
| `EntityArn` | ARN associated with the entity |
| `LastModifiedDate` | Last modified date in ISO 8601 format |
| `Details` | Stringified JSON with entity-specific details |
| `DetailsDocument` | Native JSON value of entity-specific details |

---

### 1.2 `list-entities`

Lists entities of a given type. **Paginated operation.**

**Synopsis:**
```bash
aws marketplace-catalog list-entities \
    --catalog <value> \
    --entity-type <value> \
    [--filter-list <value>] \
    [--sort <value>] \
    [--ownership-type <value>] \
    [--entity-type-filters <value>] \
    [--entity-type-sort <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog` | **Yes** | string | -- | Fixed value: `AWSMarketplace` |
| `--entity-type` | **Yes** | string | -- | Entity type: `AmiProduct`, `ContainerProduct`, `DataProduct`, `SaaSProduct`, `Offer`, `OfferSet`, `ResaleAuthorization`, `Seller`, `Experience`, `Audience`, `BrandingSettings`, `ProcurementPolicy`, `Solution` |
| `--filter-list` | No | list | None | Array of filter objects (max 8). Shorthand: `Name=string,ValueList=string,string ...` |
| `--sort` | No | structure | None | Sort criteria. Shorthand: `SortBy=string,SortOrder=ASCENDING\|DESCENDING` |
| `--ownership-type` | No | string | `SELF` | Filter by ownership: `SELF` or `SHARED` |
| `--entity-type-filters` | No | tagged union | None | Entity-type-specific filters (JSON structure) |
| `--entity-type-sort` | No | tagged union | None | Entity-type-specific sorting (JSON structure) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Entity Type Filters (tagged union — set one key):**
- `DataProductFilters`
- `SaaSProductFilters`
- `AmiProductFilters`
- `OfferFilters`
- `ContainerProductFilters`
- `ResaleAuthorizationFilters`
- `MachineLearningProductFilters`
- `OfferSetFilters`

**Output Schema:**
```json
{
    "EntitySummaryList": [
        {
            "Name": "string",
            "EntityType": "string",
            "EntityId": "string",
            "EntityArn": "string",
            "LastModifiedDate": "string",
            "Visibility": "Public|Limited|Restricted|Draft",
            "AmiProductSummary": {
                "ProductTitle": "string",
                "Visibility": "string"
            },
            "ContainerProductSummary": {
                "ProductTitle": "string",
                "Visibility": "string"
            },
            "DataProductSummary": {
                "ProductTitle": "string",
                "Visibility": "string"
            },
            "SaaSProductSummary": {
                "ProductTitle": "string",
                "Visibility": "string"
            },
            "OfferSummary": {
                "Name": "string",
                "ProductId": "string",
                "ResaleAuthorizationId": "string",
                "ReleaseDate": "string",
                "AvailabilityEndDate": "string",
                "BuyerAccounts": ["string"],
                "State": "Draft|Released",
                "Targeting": ["string"],
                "OfferSetId": "string"
            },
            "ResaleAuthorizationSummary": {
                "Name": "string",
                "ProductId": "string",
                "ProductName": "string",
                "ManufacturerAccountId": "string",
                "ManufacturerLegalName": "string",
                "ResellerAccountID": "string",
                "ResellerLegalName": "string",
                "Status": "Draft|Active|Restricted",
                "OfferExtendedStatus": "string",
                "CreatedDate": "string",
                "AvailabilityEndDate": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 1.3 `batch-describe-entities`

Returns metadata and content for multiple entities in a single batch call. Uses the same IAM permission as `DescribeEntity`.

**Synopsis:**
```bash
aws marketplace-catalog batch-describe-entities \
    --entity-request-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--entity-request-list` | **Yes** | list | -- | List of entity IDs and catalogs (1-20 items). Shorthand: `Catalog=string,EntityId=string ...` |

**Entity Request Structure:**
```json
[
    {
        "Catalog": "string",
        "EntityId": "string"
    }
]
```

**Output Schema:**
```json
{
    "EntityDetails": {
        "EntityId": {
            "EntityType": "string",
            "EntityArn": "string",
            "EntityIdentifier": "string",
            "LastModifiedDate": "string",
            "DetailsDocument": {}
        }
    },
    "Errors": {
        "EntityId": {
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    }
}
```
