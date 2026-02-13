# Directories

### 1.1 `create-directory`

Creates a Simple AD directory. Simple AD is a standalone managed directory powered by Samba 4.

**Synopsis:**
```bash
aws ds create-directory \
    --name <value> \
    --password <value> \
    --size <value> \
    [--short-name <value>] \
    [--description <value>] \
    [--vpc-settings <value>] \
    [--tags <value>] \
    [--network-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Fully qualified directory name (e.g., `corp.example.com`) |
| `--password` | **Yes** | string | -- | Administrator password (8-64 chars) |
| `--size` | **Yes** | string | -- | `Small` or `Large` |
| `--short-name` | No | string | None | NetBIOS name (e.g., `CORP`) |
| `--description` | No | string | None | Directory description (max 128 chars) |
| `--vpc-settings` | No | structure | None | VPC configuration |
| `--tags` | No | list(structure) | None | Tags. Structure: `Key=string,Value=string` |
| `--network-type` | No | string | None | `Dual-stack`, `IPv4`, or `IPv6` |

**VPC Settings Structure:**
```json
{
    "VpcId": "string",
    "SubnetIds": ["string", "string"]
}
```

**Output Schema:**
```json
{
    "DirectoryId": "string"
}
```

---

### 1.2 `create-microsoft-ad`

Creates a Managed Microsoft AD directory in AWS.

**Synopsis:**
```bash
aws ds create-microsoft-ad \
    --name <value> \
    --password <value> \
    [--short-name <value>] \
    [--description <value>] \
    --vpc-settings <value> \
    [--edition <value>] \
    [--tags <value>] \
    [--network-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Fully qualified domain name |
| `--password` | **Yes** | string | -- | Password for the Admin user (8-64 chars) |
| `--vpc-settings` | **Yes** | structure | -- | VPC configuration with VpcId and SubnetIds |
| `--short-name` | No | string | None | NetBIOS name |
| `--description` | No | string | None | Description (max 128 chars) |
| `--edition` | No | string | `Enterprise` | `Enterprise`, `Standard`, or `Hybrid` |
| `--tags` | No | list(structure) | None | Tags |
| `--network-type` | No | string | None | `Dual-stack`, `IPv4`, or `IPv6` |

**Output Schema:**
```json
{
    "DirectoryId": "string"
}
```

---

### 1.3 `delete-directory`

Deletes a directory and all of its data.

**Synopsis:**
```bash
aws ds delete-directory \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID to delete (pattern: `d-[0-9a-f]{10}`) |

**Output Schema:**
```json
{
    "DirectoryId": "string"
}
```

---

### 1.4 `describe-directories`

Returns information about directories. **Paginated operation.**

**Synopsis:**
```bash
aws ds describe-directories \
    [--directory-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-ids` | No | list(string) | All directories | Directory IDs to describe |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DirectoryDescriptions": [
        {
            "DirectoryId": "string",
            "Name": "string",
            "ShortName": "string",
            "Size": "Small|Large",
            "Edition": "Enterprise|Standard|Hybrid",
            "Alias": "string",
            "AccessUrl": "string",
            "Description": "string",
            "DnsIpAddrs": ["string"],
            "Stage": "Requested|Creating|Created|Active|Inoperable|Impaired|Restoring|RestoreFailed|Deleting|Deleted|Failed|Updating",
            "LaunchTime": "timestamp",
            "StageLastUpdatedDateTime": "timestamp",
            "Type": "SimpleAD|ADConnector|MicrosoftAD|SharedMicrosoftAD",
            "VpcSettings": {
                "VpcId": "string",
                "SubnetIds": ["string"],
                "SecurityGroupId": "string",
                "AvailabilityZones": ["string"]
            },
            "ConnectSettings": {
                "VpcId": "string",
                "SubnetIds": ["string"],
                "CustomerUserName": "string",
                "SecurityGroupId": "string",
                "ConnectIps": ["string"]
            },
            "RadiusSettings": {},
            "RadiusStatus": "Creating|Completed|Failed",
            "SsoEnabled": "boolean",
            "DesiredNumberOfDomainControllers": "integer",
            "OwnerDirectoryDescription": {},
            "RegionsInfo": {
                "PrimaryRegion": "string",
                "AdditionalRegions": ["string"]
            },
            "OsVersion": "SERVER_2012|SERVER_2019",
            "NetworkType": "Dual-stack|IPv4|IPv6"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `get-directory-limits`

Gets the directory limits for the current Region.

**Synopsis:**
```bash
aws ds get-directory-limits \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No command-specific parameters.

**Output Schema:**
```json
{
    "DirectoryLimits": {
        "CloudOnlyDirectoriesLimit": "integer",
        "CloudOnlyDirectoriesCurrentCount": "integer",
        "CloudOnlyDirectoriesLimitReached": "boolean",
        "CloudOnlyMicrosoftADLimit": "integer",
        "CloudOnlyMicrosoftADCurrentCount": "integer",
        "CloudOnlyMicrosoftADLimitReached": "boolean",
        "ConnectedDirectoriesLimit": "integer",
        "ConnectedDirectoriesCurrentCount": "integer",
        "ConnectedDirectoriesLimitReached": "boolean"
    }
}
```

---

### 1.6 `create-alias`

Creates an alias for a directory and assigns the alias to the directory. The alias must be unique.

**Synopsis:**
```bash
aws ds create-alias \
    --directory-id <value> \
    --alias <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--alias` | **Yes** | string | -- | Requested alias (must be unique) |

**Output Schema:**
```json
{
    "DirectoryId": "string",
    "Alias": "string"
}
```

---

### 1.7 `create-computer`

Creates a computer account in the specified directory.

**Synopsis:**
```bash
aws ds create-computer \
    --directory-id <value> \
    --computer-name <value> \
    --password <value> \
    [--organizational-unit-distinguished-name <value>] \
    [--computer-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--computer-name` | **Yes** | string | -- | Name of the computer account (max 15 chars) |
| `--password` | **Yes** | string | -- | Password for the computer account (8-64 chars) |
| `--organizational-unit-distinguished-name` | No | string | None | OU DN where to create the computer |
| `--computer-attributes` | No | list(structure) | None | Additional attributes. Structure: `Name=string,Value=string` |

**Output Schema:**
```json
{
    "Computer": {
        "ComputerId": "string",
        "ComputerName": "string",
        "ComputerAttributes": [
            {
                "Name": "string",
                "Value": "string"
            }
        ]
    }
}
```

---

### 1.8 `describe-settings`

Retrieves directory settings such as OS version and protocol.

**Synopsis:**
```bash
aws ds describe-settings \
    --directory-id <value> \
    [--status <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--status` | No | string | None | Filter by setting status |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DirectoryId": "string",
    "SettingEntries": [
        {
            "Type": "string",
            "Name": "string",
            "AllowedValues": "string",
            "AppliedValue": "string",
            "RequestedValue": "string",
            "RequestStatus": "string",
            "RequestDetailedStatus": {},
            "RequestStatusMessage": "string",
            "LastUpdatedDateTime": "timestamp",
            "LastRequestedDateTime": "timestamp",
            "DataType": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.9 `update-settings`

Updates directory settings.

**Synopsis:**
```bash
aws ds update-settings \
    --directory-id <value> \
    --settings <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--settings` | **Yes** | list(structure) | -- | Settings to update. Structure: `Name=string,Value=string` |

**Output Schema:**
```json
{
    "DirectoryId": "string"
}
```

---

### 1.10 `describe-domain-controllers`

Provides information about the domain controllers in a directory. **Paginated operation.**

**Synopsis:**
```bash
aws ds describe-domain-controllers \
    --directory-id <value> \
    [--domain-controller-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--domain-controller-ids` | No | list(string) | All | Filter by domain controller IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DomainControllers": [
        {
            "DirectoryId": "string",
            "DomainControllerId": "string",
            "DnsIpAddr": "string",
            "VpcId": "string",
            "SubnetId": "string",
            "AvailabilityZone": "string",
            "Status": "Creating|Active|Impaired|Restoring|Deleting|Deleted|Failed|Updating",
            "StatusReason": "string",
            "LaunchTime": "timestamp",
            "StatusLastUpdatedDateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.11 `update-number-of-domain-controllers`

Adds or removes domain controllers to/from a directory.

**Synopsis:**
```bash
aws ds update-number-of-domain-controllers \
    --directory-id <value> \
    --desired-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--desired-number` | **Yes** | integer | -- | Desired number of domain controllers (min 2) |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.12 `describe-regions`

Provides information about the regions configured for a multi-region directory. **Paginated operation.**

**Synopsis:**
```bash
aws ds describe-regions \
    --directory-id <value> \
    [--region-name <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--region-name` | No | string | None | Filter by region name |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RegionsDescription": [
        {
            "DirectoryId": "string",
            "RegionName": "string",
            "RegionType": "Primary|Additional",
            "Status": "Requested|Creating|Created|Active|Inoperable|Impaired|Restoring|RestoreFailed|Deleting|Deleted|Failed",
            "VpcSettings": {},
            "DesiredNumberOfDomainControllers": "integer",
            "LaunchTime": "timestamp",
            "StatusLastUpdatedDateTime": "timestamp",
            "LastUpdatedDateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.13 `add-region`

Adds a region to a multi-region directory.

**Synopsis:**
```bash
aws ds add-region \
    --directory-id <value> \
    --region-name <value> \
    --vpc-settings <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--region-name` | **Yes** | string | -- | AWS region to add |
| `--vpc-settings` | **Yes** | structure | -- | VPC settings for the new region |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.14 `remove-region`

Removes a region from a multi-region directory.

**Synopsis:**
```bash
aws ds remove-region \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |

**Output Schema:**

No output on success (HTTP 200).

---

### 1.15 `describe-update-directory`

Describes the status of directory updates. **Paginated operation.**

**Synopsis:**
```bash
aws ds describe-update-directory \
    --directory-id <value> \
    --update-type <value> \
    [--region-name <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--update-type` | **Yes** | string | -- | Type of update: `OS` |
| `--region-name` | No | string | None | Filter by region |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "UpdateActivities": [
        {
            "Region": "string",
            "Status": "Updated|Updating|UpdateFailed",
            "StatusReason": "string",
            "InitiatedBy": "string",
            "NewValue": {},
            "PreviousValue": {},
            "StartTime": "timestamp",
            "LastUpdatedDateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.16 `update-directory-setup`

Updates directory setup (e.g., OS version).

**Synopsis:**
```bash
aws ds update-directory-setup \
    --directory-id <value> \
    --update-type <value> \
    [--os-update-settings <value>] \
    [--create-snapshot-before-update | --no-create-snapshot-before-update] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--update-type` | **Yes** | string | -- | `OS` |
| `--os-update-settings` | No | structure | None | OS update settings. Structure: `OSVersion=SERVER_2012\|SERVER_2019` |
| `--create-snapshot-before-update` | No | boolean | None | Create snapshot before updating |

**Output Schema:**

No output on success (HTTP 200).
