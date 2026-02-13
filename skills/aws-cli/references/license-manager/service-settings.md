# Service Settings

### 7.1 `get-service-settings`

Gets the License Manager service settings for the account.

**Synopsis:**
```bash
aws license-manager get-service-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "S3BucketArn": "string",
    "SnsTopicArn": "string",
    "OrganizationConfiguration": {
        "EnableIntegration": "boolean"
    },
    "EnableCrossAccountsDiscovery": "boolean",
    "LicenseManagerResourceShareArn": "string",
    "CrossRegionDiscoveryHomeRegion": "string",
    "CrossRegionDiscoverySourceRegions": ["string"],
    "ServiceStatus": {
        "CrossAccountDiscovery": {
            "Message": "string"
        },
        "CrossRegionDiscovery": {
            "Message": {}
        }
    }
}
```

---

### 7.2 `update-service-settings`

Updates the License Manager service settings.

**Synopsis:**
```bash
aws license-manager update-service-settings \
    [--s3-bucket-arn <value>] \
    [--sns-topic-arn <value>] \
    [--organization-configuration <value>] \
    [--enable-cross-accounts-discovery | --no-enable-cross-accounts-discovery] \
    [--cross-region-discovery-home-region <value>] \
    [--cross-region-discovery-source-regions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--s3-bucket-arn` | No | string | None | S3 bucket ARN for resource inventory reports |
| `--sns-topic-arn` | No | string | None | SNS topic ARN for notifications |
| `--organization-configuration` | No | structure | None | Org integration. Shorthand: `EnableIntegration=boolean` |
| `--enable-cross-accounts-discovery` | No | boolean | None | Enable cross-account discovery |
| `--cross-region-discovery-home-region` | No | string | None | Home region for cross-region discovery |
| `--cross-region-discovery-source-regions` | No | list(string) | None | Source regions for cross-region discovery |

**Output:** None
