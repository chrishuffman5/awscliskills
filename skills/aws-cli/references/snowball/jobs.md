# Jobs

### 1.1 `create-job`

Creates a job to import or export data between Amazon S3 and your on-premises data center using a Snow Family device, or creates a local compute job.

**Synopsis:**
```bash
aws snowball create-job \
    [--job-type <value>] \
    [--resources <value>] \
    [--on-device-service-configuration <value>] \
    [--description <value>] \
    [--address-id <value>] \
    [--kms-key-arn <value>] \
    [--role-arn <value>] \
    [--snowball-capacity-preference <value>] \
    [--shipping-option <value>] \
    [--notification <value>] \
    [--cluster-id <value>] \
    [--snowball-type <value>] \
    [--forwarding-address-id <value>] \
    [--tax-documents <value>] \
    [--device-configuration <value>] \
    [--remote-management <value>] \
    [--long-term-pricing-id <value>] \
    [--impact-level <value>] \
    [--pickup-details <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-type` | No | string | None | Job type: `IMPORT`, `EXPORT`, `LOCAL_USE` |
| `--resources` | No | structure | None | S3 buckets, Lambda functions, and EC2 AMIs associated with the job |
| `--on-device-service-configuration` | No | structure | None | On-device services: NFS, Tape Gateway, EKS, S3 |
| `--description` | No | string | None | Job description (1-1024 chars) |
| `--address-id` | No | string | None | Address ID for device shipment (40 chars) |
| `--kms-key-arn` | No | string | None | KMS key ARN for data encryption |
| `--role-arn` | No | string | None | IAM role ARN for job permissions (max 255 chars) |
| `--snowball-capacity-preference` | No | string | None | Device capacity: `T50`, `T80`, `T100`, `T42`, `T98`, `T8`, `T14`, `T32`, `T240`, `T13`, `NoPreference` |
| `--shipping-option` | No | string | None | Shipping speed: `SECOND_DAY`, `NEXT_DAY`, `EXPRESS`, `STANDARD` |
| `--notification` | No | structure | None | SNS notification settings |
| `--cluster-id` | No | string | None | Cluster ID for cluster jobs (39 chars) |
| `--snowball-type` | No | string | None | Device type: `STANDARD`, `EDGE`, `EDGE_C`, `EDGE_CG`, `EDGE_S`, `SNC1_HDD`, `SNC1_SSD`, `V3_5C`, `V3_5S`, `RACK_5U_C` |
| `--forwarding-address-id` | No | string | None | Forwarding address ID (not supported in most regions) |
| `--tax-documents` | No | structure | None | Tax documents (India: GSTIN) |
| `--device-configuration` | No | structure | None | Snowcone device config (wireless connection) |
| `--remote-management` | No | string | None | Remote management: `INSTALLED_ONLY`, `INSTALLED_AUTOSTART`, `NOT_INSTALLED` |
| `--long-term-pricing-id` | No | string | None | Long-term pricing ID (41 chars) |
| `--impact-level` | No | string | None | Data impact level: `IL2`, `IL4`, `IL5`, `IL6`, `IL99` |
| `--pickup-details` | No | structure | None | Device pickup person info |

**Resources Structure:**
```json
{
    "S3Resources": [
        {
            "BucketArn": "string",
            "KeyRange": {
                "BeginMarker": "string",
                "EndMarker": "string"
            },
            "TargetOnDeviceServices": [
                {
                    "ServiceName": "NFS_ON_DEVICE_SERVICE|S3_ON_DEVICE_SERVICE",
                    "TransferOption": "IMPORT|EXPORT|LOCAL_USE"
                }
            ]
        }
    ],
    "LambdaResources": [
        {
            "LambdaArn": "string",
            "EventTriggers": [
                {
                    "EventResourceARN": "string"
                }
            ]
        }
    ],
    "Ec2AmiResources": [
        {
            "AmiId": "string",
            "SnowballAmiId": "string"
        }
    ]
}
```

**Notification Structure:**
```json
{
    "SnsTopicARN": "string",
    "JobStatesToNotify": ["New", "PreparingAppliance", "InTransitToCustomer", "WithCustomer", "Complete"],
    "NotifyAll": true|false,
    "DevicePickupSnsTopicARN": "string"
}
```

**On-Device Service Configuration:**
```json
{
    "NFSOnDeviceService": {
        "StorageLimit": "integer",
        "StorageUnit": "TB"
    },
    "TGWOnDeviceService": {
        "StorageLimit": "integer",
        "StorageUnit": "TB"
    },
    "EKSOnDeviceService": {
        "KubernetesVersion": "string",
        "EKSAnywhereVersion": "string"
    },
    "S3OnDeviceService": {
        "StorageLimit": "double",
        "StorageUnit": "TB",
        "ServiceSize": "integer",
        "FaultTolerance": "integer"
    }
}
```

**Output Schema:**
```json
{
    "JobId": "string"
}
```

---

### 1.2 `describe-job`

Returns information about a specific job including shipping details, data transfer progress, and device configuration.

**Synopsis:**
```bash
aws snowball describe-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (39 chars, pattern: `(M\|J)ID...`) |

**Output Schema:**
```json
{
    "JobMetadata": {
        "JobId": "string",
        "JobState": "New|PreparingAppliance|PreparingShipment|InTransitToCustomer|WithCustomer|InTransitToAWS|WithAWSSortingFacility|WithAWS|InProgress|Complete|Cancelled|Listing|Pending",
        "JobType": "IMPORT|EXPORT|LOCAL_USE",
        "SnowballType": "STANDARD|EDGE|EDGE_C|EDGE_CG|EDGE_S|SNC1_HDD|SNC1_SSD|V3_5C|V3_5S|RACK_5U_C",
        "CreationDate": "timestamp",
        "Resources": {
            "S3Resources": [
                {
                    "BucketArn": "string",
                    "KeyRange": {
                        "BeginMarker": "string",
                        "EndMarker": "string"
                    },
                    "TargetOnDeviceServices": []
                }
            ],
            "LambdaResources": [],
            "Ec2AmiResources": []
        },
        "Description": "string",
        "KmsKeyARN": "string",
        "RoleARN": "string",
        "AddressId": "string",
        "ShippingDetails": {
            "ShippingOption": "SECOND_DAY|NEXT_DAY|EXPRESS|STANDARD",
            "InboundShipment": {
                "Status": "string",
                "TrackingNumber": "string"
            },
            "OutboundShipment": {
                "Status": "string",
                "TrackingNumber": "string"
            }
        },
        "SnowballCapacityPreference": "T50|T80|T100|T42|T98|T8|T14|T32|T240|T13|NoPreference",
        "Notification": {
            "SnsTopicARN": "string",
            "JobStatesToNotify": ["string"],
            "NotifyAll": "boolean",
            "DevicePickupSnsTopicARN": "string"
        },
        "DataTransferProgress": {
            "BytesTransferred": "long",
            "ObjectsTransferred": "long",
            "TotalBytes": "long",
            "TotalObjects": "long"
        },
        "JobLogInfo": {
            "JobCompletionReportURI": "string",
            "JobSuccessLogURI": "string",
            "JobFailureLogURI": "string"
        },
        "ClusterId": "string",
        "ForwardingAddressId": "string",
        "TaxDocuments": {
            "IND": {
                "GSTIN": "string"
            }
        },
        "DeviceConfiguration": {
            "SnowconeDeviceConfiguration": {
                "WirelessConnection": {
                    "IsWifiEnabled": "boolean"
                }
            }
        },
        "RemoteManagement": "INSTALLED_ONLY|INSTALLED_AUTOSTART|NOT_INSTALLED",
        "LongTermPricingId": "string",
        "OnDeviceServiceConfiguration": {
            "NFSOnDeviceService": {
                "StorageLimit": "integer",
                "StorageUnit": "TB"
            },
            "TGWOnDeviceService": {
                "StorageLimit": "integer",
                "StorageUnit": "TB"
            },
            "EKSOnDeviceService": {
                "KubernetesVersion": "string",
                "EKSAnywhereVersion": "string"
            },
            "S3OnDeviceService": {
                "StorageLimit": "double",
                "StorageUnit": "TB",
                "ServiceSize": "integer",
                "FaultTolerance": "integer"
            }
        },
        "ImpactLevel": "IL2|IL4|IL5|IL6|IL99",
        "PickupDetails": {
            "Name": "string",
            "PhoneNumber": "string",
            "Email": "string",
            "IdentificationNumber": "string",
            "IdentificationExpirationDate": "timestamp",
            "IdentificationIssuingOrg": "string",
            "DevicePickupId": "string"
        },
        "SnowballId": "string"
    },
    "SubJobMetadata": []
}
```

---

### 1.3 `update-job`

Updates an existing job. Only available while the job's `JobState` is `New` (typically within 60 minutes of creation).

**Synopsis:**
```bash
aws snowball update-job \
    --job-id <value> \
    [--role-arn <value>] \
    [--notification <value>] \
    [--resources <value>] \
    [--on-device-service-configuration <value>] \
    [--address-id <value>] \
    [--shipping-option <value>] \
    [--description <value>] \
    [--snowball-capacity-preference <value>] \
    [--forwarding-address-id <value>] \
    [--pickup-details <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID to update (39 chars) |
| `--role-arn` | No | string | None | New IAM role ARN (max 255 chars) |
| `--notification` | No | structure | None | Updated SNS notification settings |
| `--resources` | No | structure | None | Updated S3, Lambda, or EC2 AMI resources |
| `--on-device-service-configuration` | No | structure | None | Updated on-device services |
| `--address-id` | No | string | None | Updated shipping address ID (40 chars) |
| `--shipping-option` | No | string | None | Updated shipping speed: `SECOND_DAY`, `NEXT_DAY`, `EXPRESS`, `STANDARD` |
| `--description` | No | string | None | Updated description (1-1024 chars) |
| `--snowball-capacity-preference` | No | string | None | Updated capacity preference |
| `--forwarding-address-id` | No | string | None | Updated forwarding address ID |
| `--pickup-details` | No | structure | None | Updated pickup person details |

**Output:** None

---

### 1.4 `cancel-job`

Cancels the specified job. Jobs can only be cancelled before the `JobState` changes to `PreparingAppliance`.

**Synopsis:**
```bash
aws snowball cancel-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID to cancel (39 chars) |

**Output:** None

---

### 1.5 `list-jobs`

Returns an array of `JobListEntry` objects for all jobs in the account. **Paginated operation.**

**Synopsis:**
```bash
aws snowball list-jobs \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "JobListEntries": [
        {
            "JobId": "string",
            "JobState": "New|PreparingAppliance|PreparingShipment|InTransitToCustomer|WithCustomer|InTransitToAWS|WithAWSSortingFacility|WithAWS|InProgress|Complete|Cancelled|Listing|Pending",
            "IsMaster": "boolean",
            "JobType": "IMPORT|EXPORT|LOCAL_USE",
            "SnowballType": "STANDARD|EDGE|EDGE_C|EDGE_CG|EDGE_S|SNC1_HDD|SNC1_SSD|V3_5C|V3_5S|RACK_5U_C",
            "CreationDate": "timestamp",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.6 `get-job-manifest`

Returns the presigned Amazon S3 URL for the manifest file associated with the specified job. The manifest is only available when the job is in the `WithCustomer` state. The presigned URL is valid for 60 minutes.

**Synopsis:**
```bash
aws snowball get-job-manifest \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (39 chars) |

**Output Schema:**
```json
{
    "ManifestURI": "string"
}
```

---

### 1.7 `get-job-unlock-code`

Returns the unlock code for the specified job. The unlock code is a 29-character code (25 alphanumeric + 4 hyphens) used to decrypt the manifest file. Valid for up to 360 days after job creation.

**Synopsis:**
```bash
aws snowball get-job-unlock-code \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (39 chars) |

**Output Schema:**
```json
{
    "UnlockCode": "string"
}
```

---

### 1.8 `get-software-updates`

Returns the presigned Amazon S3 URL for software updates for a Snow device. The URL is available 2 days after the request.

**Synopsis:**
```bash
aws snowball get-software-updates \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (39 chars) |

**Output Schema:**
```json
{
    "UpdatesURI": "string"
}
```

---

### 1.9 `update-job-shipment-state`

Updates the state of a job's shipment. Used to confirm device receipt or return.

**Synopsis:**
```bash
aws snowball update-job-shipment-state \
    --job-id <value> \
    --shipment-state <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (39 chars) |
| `--shipment-state` | **Yes** | string | -- | Shipment state: `RECEIVED`, `RETURNED` |

**Output:** None
