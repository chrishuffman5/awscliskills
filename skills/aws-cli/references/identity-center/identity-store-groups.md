# Identity Store Groups

Commands use the `aws identitystore` namespace.

### 10.1 `create-group`

Creates a new group in the identity store.

**Synopsis:**
```bash
aws identitystore create-group \
    --identity-store-id <value> \
    --display-name <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--display-name` | **Yes** | string | -- | Group display name (1-1024 chars) |
| `--description` | No | string | None | Group description (1-1024 chars) |

**Output Schema:**
```json
{
    "GroupId": "string",
    "IdentityStoreId": "string"
}
```

---

### 10.2 `delete-group`

Deletes a group from the identity store.

**Synopsis:**
```bash
aws identitystore delete-group \
    --identity-store-id <value> \
    --group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--group-id` | **Yes** | string | -- | GUID of the group to delete |

**Output Schema:**

No output on success (HTTP 200).

---

### 10.3 `describe-group`

Retrieves details about a specific group.

**Synopsis:**
```bash
aws identitystore describe-group \
    --identity-store-id <value> \
    --group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--group-id` | **Yes** | string | -- | GUID of the group |

**Output Schema:**
```json
{
    "GroupId": "string",
    "DisplayName": "string",
    "ExternalIds": [
        {
            "Issuer": "string",
            "Id": "string"
        }
    ],
    "Description": "string",
    "IdentityStoreId": "string"
}
```

---

### 10.4 `update-group`

Updates a group's attributes in the identity store.

**Synopsis:**
```bash
aws identitystore update-group \
    --identity-store-id <value> \
    --group-id <value> \
    --operations <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--group-id` | **Yes** | string | -- | GUID of the group |
| `--operations` | **Yes** | list(structure) | -- | Update operations. Structure: `AttributePath=string,AttributeValue=string` |

**Output Schema:**

No output on success (HTTP 200).

---

### 10.5 `get-group-id`

Looks up a group ID by an alternate identifier.

**Synopsis:**
```bash
aws identitystore get-group-id \
    --identity-store-id <value> \
    --alternate-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--alternate-identifier` | **Yes** | tagged union | -- | Alternate identifier to look up |

**Alternate Identifier Structure (tagged union — set one):**
```json
{
    "UniqueAttribute": {
        "AttributePath": "string",
        "AttributeValue": "string"
    }
}
```
or
```json
{
    "ExternalId": {
        "Issuer": "string",
        "Id": "string"
    }
}
```

**Output Schema:**
```json
{
    "GroupId": "string",
    "IdentityStoreId": "string"
}
```

---

### 10.6 `list-groups`

Lists all groups in the identity store. **Paginated operation.**

**Synopsis:**
```bash
aws identitystore list-groups \
    --identity-store-id <value> \
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
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--filters` | No | list(structure) | None | Filters. Structure: `AttributePath=string,AttributeValue=string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Groups": [
        {
            "GroupId": "string",
            "DisplayName": "string",
            "ExternalIds": [],
            "Description": "string",
            "IdentityStoreId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.7 `create-group-membership`

Adds a member to a group.

**Synopsis:**
```bash
aws identitystore create-group-membership \
    --identity-store-id <value> \
    --group-id <value> \
    --member-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--group-id` | **Yes** | string | -- | GUID of the group |
| `--member-id` | **Yes** | tagged union | -- | Member identifier. Structure: `UserId=string` |

**Output Schema:**
```json
{
    "MembershipId": "string",
    "IdentityStoreId": "string"
}
```

---

### 10.8 `delete-group-membership`

Removes a member from a group.

**Synopsis:**
```bash
aws identitystore delete-group-membership \
    --identity-store-id <value> \
    --membership-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--membership-id` | **Yes** | string | -- | GUID of the membership to remove |

**Output Schema:**

No output on success (HTTP 200).

---

### 10.9 `describe-group-membership`

Retrieves details about a group membership.

**Synopsis:**
```bash
aws identitystore describe-group-membership \
    --identity-store-id <value> \
    --membership-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--membership-id` | **Yes** | string | -- | GUID of the membership |

**Output Schema:**
```json
{
    "IdentityStoreId": "string",
    "MembershipId": "string",
    "GroupId": "string",
    "MemberId": {
        "UserId": "string"
    }
}
```

---

### 10.10 `get-group-membership-id`

Looks up a group membership ID.

**Synopsis:**
```bash
aws identitystore get-group-membership-id \
    --identity-store-id <value> \
    --group-id <value> \
    --member-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--group-id` | **Yes** | string | -- | GUID of the group |
| `--member-id` | **Yes** | tagged union | -- | Member identifier. Structure: `UserId=string` |

**Output Schema:**
```json
{
    "MembershipId": "string",
    "IdentityStoreId": "string"
}
```

---

### 10.11 `is-member-in-groups`

Checks if a member is in the specified groups.

**Synopsis:**
```bash
aws identitystore is-member-in-groups \
    --identity-store-id <value> \
    --member-id <value> \
    --group-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--member-id` | **Yes** | tagged union | -- | Member identifier. Structure: `UserId=string` |
| `--group-ids` | **Yes** | list(string) | -- | List of group GUIDs to check (max 25) |

**Output Schema:**
```json
{
    "Results": [
        {
            "GroupId": "string",
            "MemberId": {
                "UserId": "string"
            },
            "MembershipExists": "boolean"
        }
    ]
}
```

---

### 10.12 `list-group-memberships`

Lists all members in a group. **Paginated operation.**

**Synopsis:**
```bash
aws identitystore list-group-memberships \
    --identity-store-id <value> \
    --group-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--group-id` | **Yes** | string | -- | GUID of the group |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GroupMemberships": [
        {
            "IdentityStoreId": "string",
            "MembershipId": "string",
            "GroupId": "string",
            "MemberId": {
                "UserId": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 10.13 `list-group-memberships-for-member`

Lists all groups a member belongs to. **Paginated operation.**

**Synopsis:**
```bash
aws identitystore list-group-memberships-for-member \
    --identity-store-id <value> \
    --member-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--member-id` | **Yes** | tagged union | -- | Member identifier. Structure: `UserId=string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GroupMemberships": [
        {
            "IdentityStoreId": "string",
            "MembershipId": "string",
            "GroupId": "string",
            "MemberId": {
                "UserId": "string"
            }
        }
    ],
    "NextToken": "string"
}
```
