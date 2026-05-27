# Patch Baselines

### 6.1 `create-patch-baseline`

Creates a patch baseline that defines which patches are approved for installation on your instances.

**Synopsis:**
```bash
aws ssm create-patch-baseline \
    --name <value> \
    [--operating-system <value>] \
    [--global-filters <value>] \
    [--approval-rules <value>] \
    [--approved-patches <value>] \
    [--approved-patches-compliance-level <value>] \
    [--approved-patches-enable-non-security | --no-approved-patches-enable-non-security] \
    [--rejected-patches <value>] \
    [--rejected-patches-action <value>] \
    [--description <value>] \
    [--sources <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Patch baseline name |
| `--operating-system` | No | string | `WINDOWS` | OS: `WINDOWS`, `AMAZON_LINUX`, `AMAZON_LINUX_2`, `AMAZON_LINUX_2022`, `AMAZON_LINUX_2023`, `UBUNTU`, `REDHAT_ENTERPRISE_LINUX`, `SUSE`, `CENTOS`, `ORACLE_LINUX`, `DEBIAN`, `MACOS`, `RASPBIAN`, `ROCKY_LINUX`, `ALMA_LINUX` |
| `--global-filters` | No | structure | None | Global patch filters |
| `--approval-rules` | No | structure | None | Patch approval rules |
| `--approved-patches` | No | list(string) | None | Explicitly approved patch IDs |
| `--approved-patches-compliance-level` | No | string | `UNSPECIFIED` | Compliance level: `CRITICAL`, `HIGH`, `MEDIUM`, `LOW`, `INFORMATIONAL`, `UNSPECIFIED` |
| `--rejected-patches` | No | list(string) | None | Explicitly rejected patch IDs |
| `--rejected-patches-action` | No | string | `ALLOW_AS_DEPENDENCY` | Action for rejected patches: `ALLOW_AS_DEPENDENCY` or `BLOCK` |
| `--description` | No | string | None | Description |
| `--sources` | No | list | None | Patch source repositories |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Approval Rules Structure:**
```json
{
    "PatchRules": [
        {
            "PatchFilterGroup": {
                "PatchFilters": [
                    {
                        "Key": "ARCH|ADVISORY_ID|BUGZILLA_ID|CLASSIFICATION|CVE_ID|EPOCH|MSRC_SEVERITY|NAME|PATCH_ID|PATCH_SET|PRIORITY|PRODUCT|PRODUCT_FAMILY|RELEASE|REPOSITORY|SECTION|SECURITY|SEVERITY|VERSION",
                        "Values": ["string"]
                    }
                ]
            },
            "ComplianceLevel": "CRITICAL|HIGH|MEDIUM|LOW|INFORMATIONAL|UNSPECIFIED",
            "ApproveAfterDays": "integer",
            "ApproveUntilDate": "string",
            "EnableNonSecurity": true
        }
    ]
}
```

**Output Schema:**
```json
{
    "BaselineId": "string"
}
```

---

### 6.2 `delete-patch-baseline`

Deletes a patch baseline.

**Synopsis:**
```bash
aws ssm delete-patch-baseline \
    --baseline-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--baseline-id` | **Yes** | string | -- | Patch baseline ID |

**Output Schema:**
```json
{
    "BaselineId": "string"
}
```

---

### 6.3 `describe-patch-baselines`

Lists patch baselines. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-patch-baselines \
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
| `--filters` | No | list | None | Filters: `NAME_PREFIX`, `OWNER`, `OPERATING_SYSTEM` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "BaselineIdentities": [
        {
            "BaselineId": "string",
            "BaselineName": "string",
            "OperatingSystem": "string",
            "BaselineDescription": "string",
            "DefaultBaseline": true
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `get-patch-baseline`

Gets detailed information about a patch baseline.

**Synopsis:**
```bash
aws ssm get-patch-baseline \
    --baseline-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--baseline-id` | **Yes** | string | -- | Patch baseline ID |

**Output Schema:**
```json
{
    "BaselineId": "string",
    "Name": "string",
    "OperatingSystem": "string",
    "GlobalFilters": {
        "PatchFilters": []
    },
    "ApprovalRules": {
        "PatchRules": []
    },
    "ApprovedPatches": ["string"],
    "ApprovedPatchesComplianceLevel": "string",
    "ApprovedPatchesEnableNonSecurity": true,
    "RejectedPatches": ["string"],
    "RejectedPatchesAction": "ALLOW_AS_DEPENDENCY|BLOCK",
    "PatchGroups": ["string"],
    "CreatedDate": "timestamp",
    "ModifiedDate": "timestamp",
    "Description": "string",
    "Sources": []
}
```

---

### 6.5 `update-patch-baseline`

Updates a patch baseline configuration.

**Synopsis:**
```bash
aws ssm update-patch-baseline \
    --baseline-id <value> \
    [--name <value>] \
    [--global-filters <value>] \
    [--approval-rules <value>] \
    [--approved-patches <value>] \
    [--approved-patches-compliance-level <value>] \
    [--rejected-patches <value>] \
    [--rejected-patches-action <value>] \
    [--description <value>] \
    [--sources <value>] \
    [--replace | --no-replace] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--baseline-id` | **Yes** | string | -- | Patch baseline ID |
| `--name` | No | string | None | Updated name |
| `--global-filters` | No | structure | None | Updated global filters |
| `--approval-rules` | No | structure | None | Updated approval rules |
| `--approved-patches` | No | list(string) | None | Updated approved patches |
| `--approved-patches-compliance-level` | No | string | None | Updated compliance level |
| `--rejected-patches` | No | list(string) | None | Updated rejected patches |
| `--rejected-patches-action` | No | string | None | Updated rejected action |
| `--description` | No | string | None | Updated description |
| `--sources` | No | list | None | Updated patch sources |
| `--replace` | No | boolean | false | Replace all lists with provided values |

**Output Schema:**
```json
{
    "BaselineId": "string",
    "Name": "string",
    "OperatingSystem": "string",
    "GlobalFilters": {},
    "ApprovalRules": {},
    "ApprovedPatches": ["string"],
    "ApprovedPatchesComplianceLevel": "string",
    "RejectedPatches": ["string"],
    "RejectedPatchesAction": "string",
    "CreatedDate": "timestamp",
    "ModifiedDate": "timestamp",
    "Description": "string",
    "Sources": []
}
```

---

### 6.6 `register-patch-baseline-for-patch-group`

Registers a patch baseline for a patch group.

**Synopsis:**
```bash
aws ssm register-patch-baseline-for-patch-group \
    --baseline-id <value> \
    --patch-group <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--baseline-id` | **Yes** | string | -- | Patch baseline ID |
| `--patch-group` | **Yes** | string | -- | Patch group name |

**Output Schema:**
```json
{
    "BaselineId": "string",
    "PatchGroup": "string"
}
```

---

### 6.7 `deregister-patch-baseline-for-patch-group`

Removes a patch baseline from a patch group.

**Synopsis:**
```bash
aws ssm deregister-patch-baseline-for-patch-group \
    --baseline-id <value> \
    --patch-group <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--baseline-id` | **Yes** | string | -- | Patch baseline ID |
| `--patch-group` | **Yes** | string | -- | Patch group name |

**Output Schema:**
```json
{
    "BaselineId": "string",
    "PatchGroup": "string"
}
```

---

### 6.8 `describe-patch-groups`

Lists all patch groups that have been registered with patch baselines. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-patch-groups \
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
| `--filters` | No | list | None | Filters: `NAME_PREFIX`, `OPERATING_SYSTEM` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Mappings": [
        {
            "PatchGroup": "string",
            "BaselineIdentity": {
                "BaselineId": "string",
                "BaselineName": "string",
                "OperatingSystem": "string",
                "BaselineDescription": "string",
                "DefaultBaseline": true
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 6.9 `describe-patch-group-state`

Returns aggregate patch compliance summary for a patch group.

**Synopsis:**
```bash
aws ssm describe-patch-group-state \
    --patch-group <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--patch-group` | **Yes** | string | -- | Patch group name |

**Output Schema:**
```json
{
    "Instances": "integer",
    "InstancesWithInstalledPatches": "integer",
    "InstancesWithInstalledOtherPatches": "integer",
    "InstancesWithInstalledPendingRebootPatches": "integer",
    "InstancesWithInstalledRejectedPatches": "integer",
    "InstancesWithMissingPatches": "integer",
    "InstancesWithFailedPatches": "integer",
    "InstancesWithNotApplicablePatches": "integer",
    "InstancesWithUnreportedNotApplicablePatches": "integer",
    "InstancesWithCriticalNonCompliantPatches": "integer",
    "InstancesWithSecurityNonCompliantPatches": "integer",
    "InstancesWithOtherNonCompliantPatches": "integer"
}
```

---

### 6.10 `describe-instance-patch-states`

Returns the patch state for specified instances. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-instance-patch-states \
    --instance-ids <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-ids` | **Yes** | list(string) | -- | Instance IDs (max 50) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "InstancePatchStates": [
        {
            "InstanceId": "string",
            "PatchGroup": "string",
            "BaselineId": "string",
            "SnapshotId": "string",
            "InstallOverrideList": "string",
            "OwnerInformation": "string",
            "InstalledCount": "integer",
            "InstalledOtherCount": "integer",
            "InstalledPendingRebootCount": "integer",
            "InstalledRejectedCount": "integer",
            "MissingCount": "integer",
            "FailedCount": "integer",
            "UnreportedNotApplicableCount": "integer",
            "NotApplicableCount": "integer",
            "OperationStartTime": "timestamp",
            "OperationEndTime": "timestamp",
            "Operation": "Scan|Install",
            "RebootOption": "RebootIfNeeded|NoReboot",
            "SecurityNonCompliantCount": "integer",
            "CriticalNonCompliantCount": "integer",
            "OtherNonCompliantCount": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.11 `describe-instance-patches`

Lists patches applied to or missing from a specific instance. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-instance-patches \
    --instance-id <value> \
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
| `--instance-id` | **Yes** | string | -- | Instance ID |
| `--filters` | No | list | None | Filters: `State`, `Classification`, `Severity` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Patches": [
        {
            "Title": "string",
            "KBId": "string",
            "Classification": "string",
            "Severity": "string",
            "State": "INSTALLED|INSTALLED_OTHER|INSTALLED_PENDING_REBOOT|INSTALLED_REJECTED|MISSING|NOT_APPLICABLE|FAILED",
            "InstalledTime": "timestamp",
            "CVEIds": "string"
        }
    ],
    "NextToken": "string"
}
```
