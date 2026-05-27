# Users

### 5.1 `create-user`

Creates a user account for the specified instance.

**Synopsis:**
```bash
aws connect create-user \
    --username <value> \
    --security-profile-ids <value> \
    --routing-profile-id <value> \
    --instance-id <value> \
    [--password <value>] \
    [--identity-info <value>] \
    [--phone-config <value>] \
    [--directory-user-id <value>] \
    [--hierarchy-group-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--username` | **Yes** | string | -- | Username (1-100 chars) |
| `--security-profile-ids` | **Yes** | list | -- | Security profile IDs (1-10) |
| `--routing-profile-id` | **Yes** | string | -- | Routing profile ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--password` | No | string | None | Password (required for CONNECT_MANAGED) |
| `--identity-info` | No | structure | None | `FirstName`, `LastName`, `Email`, `SecondaryEmail`, `Mobile` |
| `--phone-config` | No | structure | None | `PhoneType` (SOFT_PHONE/DESK_PHONE), `AutoAccept`, `AfterContactWorkTimeLimit`, `DeskPhoneNumber` |
| `--directory-user-id` | No | string | None | Directory user ID |
| `--hierarchy-group-id` | No | string | None | Hierarchy group ID |
| `--tags` | No | map | None | Tags (max 50) |

**IdentityInfo:**
```json
{
    "FirstName": "string",
    "LastName": "string",
    "Email": "string",
    "SecondaryEmail": "string",
    "Mobile": "string"
}
```

**PhoneConfig:**
```json
{
    "PhoneType": "SOFT_PHONE|DESK_PHONE",
    "AutoAccept": "boolean",
    "AfterContactWorkTimeLimit": "integer",
    "DeskPhoneNumber": "string"
}
```

**Output Schema:**
```json
{
    "UserId": "string",
    "UserArn": "string"
}
```

---

### 5.2 `describe-user`

Describes a user.

**Synopsis:**
```bash
aws connect describe-user \
    --user-id <value> \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-id` | **Yes** | string | -- | User ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output Schema:**
```json
{
    "User": {
        "Id": "string",
        "Arn": "string",
        "Username": "string",
        "IdentityInfo": { "FirstName": "string", "LastName": "string", "Email": "string", "SecondaryEmail": "string", "Mobile": "string" },
        "PhoneConfig": { "PhoneType": "string", "AutoAccept": "boolean", "AfterContactWorkTimeLimit": "integer", "DeskPhoneNumber": "string" },
        "DirectoryUserId": "string",
        "SecurityProfileIds": ["string"],
        "RoutingProfileId": "string",
        "HierarchyGroupId": "string",
        "Tags": { "key": "value" },
        "LastModifiedTime": "timestamp",
        "LastModifiedRegion": "string"
    }
}
```

---

### 5.3 `list-users`

Lists users. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-users \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

**Output Schema:**
```json
{
    "UserSummaryList": [
        { "Id": "string", "Arn": "string", "Username": "string", "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `update-user-config`

Updates user configuration settings.

**Synopsis:**
```bash
aws connect update-user-config \
    --instance-id <value> \
    --user-id <value> \
    --telephony-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--user-id` | **Yes** | string | -- | User ID |
| `--telephony-config` | **Yes** | structure | -- | Updated telephony config with distributions |

**Output:** None

---

### 5.5 `update-user-hierarchy`

Assigns a user to a hierarchy group.

**Synopsis:**
```bash
aws connect update-user-hierarchy \
    --instance-id <value> \
    --user-id <value> \
    [--hierarchy-group-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--user-id` | **Yes** | string | -- | User ID |
| `--hierarchy-group-id` | No | string | None | Hierarchy group ID (omit to unassign) |

**Output:** None

---

### 5.6 `update-user-identity-info`

Updates user identity information.

**Synopsis:**
```bash
aws connect update-user-identity-info \
    --identity-info <value> \
    --user-id <value> \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-info` | **Yes** | structure | -- | Updated identity info |
| `--user-id` | **Yes** | string | -- | User ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output:** None

---

### 5.7 `update-user-phone-config`

Updates user phone configuration.

**Synopsis:**
```bash
aws connect update-user-phone-config \
    --phone-config <value> \
    --user-id <value> \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--phone-config` | **Yes** | structure | -- | Updated phone config |
| `--user-id` | **Yes** | string | -- | User ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output:** None

---

### 5.8 `update-user-routing-profile`

Updates a user's routing profile.

**Synopsis:**
```bash
aws connect update-user-routing-profile \
    --routing-profile-id <value> \
    --user-id <value> \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--routing-profile-id` | **Yes** | string | -- | New routing profile ID |
| `--user-id` | **Yes** | string | -- | User ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output:** None

---

### 5.9 `update-user-security-profiles`

Updates a user's security profiles.

**Synopsis:**
```bash
aws connect update-user-security-profiles \
    --security-profile-ids <value> \
    --user-id <value> \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--security-profile-ids` | **Yes** | list | -- | New security profile IDs (1-10) |
| `--user-id` | **Yes** | string | -- | User ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output:** None

---

### 5.10 `delete-user`

Deletes a user.

**Synopsis:**
```bash
aws connect delete-user \
    --instance-id <value> \
    --user-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--user-id` | **Yes** | string | -- | User ID |

**Output:** None

---

### 5.11 `put-user-status`

Sets the state of a user to the specified status.

**Synopsis:**
```bash
aws connect put-user-status \
    --user-id <value> \
    --instance-id <value> \
    --agent-status-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-id` | **Yes** | string | -- | User ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--agent-status-id` | **Yes** | string | -- | Agent status ID |

**Output:** None

---

### 5.12 `get-current-user-data`

Gets current user data including status and active contacts.

**Synopsis:**
```bash
aws connect get-current-user-data \
    --instance-id <value> \
    --filters <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--filters` | **Yes** | structure | -- | Filters with Queues, ContactFilter, RoutingProfiles, Agents, UserHierarchyGroups |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

**Output Schema:**
```json
{
    "UserDataList": [
        {
            "User": { "Id": "string", "Arn": "string" },
            "RoutingProfile": { "Id": "string", "Arn": "string" },
            "HierarchyPath": {},
            "Status": { "StatusStartTimestamp": "timestamp", "StatusArn": "string", "StatusName": "string" },
            "AvailableSlotsByChannel": { "VOICE": "integer", "CHAT": "integer" },
            "MaxSlotsByChannel": { "VOICE": "integer", "CHAT": "integer" },
            "ActiveSlotsByChannel": { "VOICE": "integer", "CHAT": "integer" },
            "Contacts": [ { "ContactId": "string", "Channel": "string", "InitiationMethod": "string", "AgentContactState": "string", "StateStartTimestamp": "timestamp", "ConnectedToAgentTimestamp": "timestamp", "Queue": {} } ],
            "NextStatus": "string"
        }
    ],
    "NextToken": "string",
    "ApproximateTotalCount": "long"
}
```

---

### 5.13 `search-users`

Searches users. **Paginated operation.**

**Synopsis:**
```bash
aws connect search-users \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--search-filter <value>] \
    [--search-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-filter` | No | structure | None | Tag filter |
| `--search-criteria` | No | structure | None | Search criteria |

**Output Schema:**
```json
{
    "Users": [ { "Arn": "string", "DirectoryUserId": "string", "HierarchyGroupId": "string", "Id": "string", "IdentityInfo": {}, "PhoneConfig": {}, "RoutingProfileId": "string", "SecurityProfileIds": [], "Tags": {}, "Username": "string" } ],
    "NextToken": "string",
    "ApproximateTotalCount": "long"
}
```

---

### 5.14 `create-user-hierarchy-group`

Creates a new hierarchy group.

**Synopsis:**
```bash
aws connect create-user-hierarchy-group \
    --name <value> \
    --instance-id <value> \
    [--parent-group-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Group name |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--parent-group-id` | No | string | None | Parent group ID for nesting |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "HierarchyGroupId": "string",
    "HierarchyGroupArn": "string"
}
```

---

### 5.15 `describe-user-hierarchy-group`

Describes a hierarchy group.

**Synopsis:**
```bash
aws connect describe-user-hierarchy-group \
    --hierarchy-group-id <value> \
    --instance-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hierarchy-group-id` | **Yes** | string | -- | Hierarchy group ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |

**Output Schema:**
```json
{
    "HierarchyGroup": {
        "Id": "string", "Arn": "string", "Name": "string",
        "LevelId": "string",
        "HierarchyPath": {
            "LevelOne": { "Id": "string", "Arn": "string", "Name": "string" },
            "LevelTwo": {}, "LevelThree": {}, "LevelFour": {}, "LevelFive": {}
        },
        "Tags": { "key": "value" },
        "LastModifiedTime": "timestamp",
        "LastModifiedRegion": "string"
    }
}
```

---

### 5.16 `list-user-hierarchy-groups`

Lists hierarchy groups. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-user-hierarchy-groups \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

**Output Schema:**
```json
{
    "UserHierarchyGroupSummaryList": [ { "Id": "string", "Arn": "string", "Name": "string", "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" } ],
    "NextToken": "string"
}
```

---

### 5.17-5.20 Hierarchy Group Management

`update-user-hierarchy-group-name`, `delete-user-hierarchy-group`, `describe-user-hierarchy-structure`, `update-user-hierarchy-structure`, `search-user-hierarchy-groups` follow the same pattern requiring `--instance-id` and the relevant hierarchy group/structure parameters.

---

### 5.21 `associate-user-proficiencies`

Associates proficiency attributes with a user.

**Synopsis:**
```bash
aws connect associate-user-proficiencies \
    --instance-id <value> \
    --user-id <value> \
    --user-proficiencies <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--user-id` | **Yes** | string | -- | User ID |
| `--user-proficiencies` | **Yes** | list | -- | List of proficiency objects with `AttributeName`, `AttributeValue`, `Level` |

**Output:** None

---

### 5.22 `list-user-proficiencies`

Lists user proficiencies. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-user-proficiencies \
    --instance-id <value> \
    --user-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--user-id` | **Yes** | string | -- | User ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "UserProficiencyList": [ { "AttributeName": "string", "AttributeValue": "string", "Level": "float" } ],
    "NextToken": "string",
    "LastModifiedTime": "timestamp",
    "LastModifiedRegion": "string"
}
```

---

### 5.23 `update-user-proficiencies`

Updates user proficiency levels.

**Synopsis:**
```bash
aws connect update-user-proficiencies \
    --instance-id <value> \
    --user-id <value> \
    --user-proficiencies <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--user-id` | **Yes** | string | -- | User ID |
| `--user-proficiencies` | **Yes** | list | -- | Updated proficiencies |

**Output:** None

---

### 5.24 `disassociate-user-proficiencies`

Removes proficiency attributes from a user.

**Synopsis:**
```bash
aws connect disassociate-user-proficiencies \
    --instance-id <value> \
    --user-id <value> \
    --user-proficiencies <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--user-id` | **Yes** | string | -- | User ID |
| `--user-proficiencies` | **Yes** | list | -- | Proficiencies to remove |

**Output:** None
