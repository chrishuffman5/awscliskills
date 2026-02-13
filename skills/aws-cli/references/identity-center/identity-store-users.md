# Identity Store Users

Commands use the `aws identitystore` namespace.

### 9.1 `create-user`

Creates a new user in the identity store.

**Synopsis:**
```bash
aws identitystore create-user \
    --identity-store-id <value> \
    [--user-name <value>] \
    [--name <value>] \
    [--display-name <value>] \
    [--nick-name <value>] \
    [--profile-url <value>] \
    [--emails <value>] \
    [--addresses <value>] \
    [--phone-numbers <value>] \
    [--user-type <value>] \
    [--title <value>] \
    [--preferred-language <value>] \
    [--locale <value>] \
    [--timezone <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store (e.g., `d-1234567890`) |
| `--user-name` | No | string | None | Unique username (1-128 chars) |
| `--name` | No | structure | None | Name object with GivenName, FamilyName, etc. |
| `--display-name` | No | string | None | Display name (1-1024 chars) |
| `--nick-name` | No | string | None | Nickname (1-1024 chars) |
| `--profile-url` | No | string | None | Profile URL |
| `--emails` | No | list(structure) | None | Email addresses (max 1). Structure: `Value=string,Type=string,Primary=boolean` |
| `--addresses` | No | list(structure) | None | Addresses (max 1) |
| `--phone-numbers` | No | list(structure) | None | Phone numbers (max 1). Structure: `Value=string,Type=string,Primary=boolean` |
| `--user-type` | No | string | None | User type |
| `--title` | No | string | None | Job title |
| `--preferred-language` | No | string | None | Preferred language |
| `--locale` | No | string | None | Geographical locale |
| `--timezone` | No | string | None | Time zone |

**Name Structure:**
```json
{
    "Formatted": "string",
    "FamilyName": "string",
    "GivenName": "string",
    "MiddleName": "string",
    "HonorificPrefix": "string",
    "HonorificSuffix": "string"
}
```

**Output Schema:**
```json
{
    "UserId": "string",
    "IdentityStoreId": "string"
}
```

---

### 9.2 `delete-user`

Deletes a user from the identity store.

**Synopsis:**
```bash
aws identitystore delete-user \
    --identity-store-id <value> \
    --user-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--user-id` | **Yes** | string | -- | GUID of the user to delete |

**Output Schema:**

No output on success (HTTP 200).

---

### 9.3 `describe-user`

Retrieves details about a specific user.

**Synopsis:**
```bash
aws identitystore describe-user \
    --identity-store-id <value> \
    --user-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--user-id` | **Yes** | string | -- | GUID of the user |

**Output Schema:**
```json
{
    "UserName": "string",
    "UserId": "string",
    "ExternalIds": [
        {
            "Issuer": "string",
            "Id": "string"
        }
    ],
    "Name": {
        "Formatted": "string",
        "FamilyName": "string",
        "GivenName": "string",
        "MiddleName": "string",
        "HonorificPrefix": "string",
        "HonorificSuffix": "string"
    },
    "DisplayName": "string",
    "NickName": "string",
    "ProfileUrl": "string",
    "Emails": [
        {
            "Value": "string",
            "Type": "string",
            "Primary": "boolean"
        }
    ],
    "Addresses": [
        {
            "StreetAddress": "string",
            "Locality": "string",
            "Region": "string",
            "PostalCode": "string",
            "Country": "string",
            "Formatted": "string",
            "Type": "string",
            "Primary": "boolean"
        }
    ],
    "PhoneNumbers": [
        {
            "Value": "string",
            "Type": "string",
            "Primary": "boolean"
        }
    ],
    "UserType": "string",
    "Title": "string",
    "PreferredLanguage": "string",
    "Locale": "string",
    "Timezone": "string",
    "IdentityStoreId": "string"
}
```

---

### 9.4 `update-user`

Updates a user's attributes in the identity store.

**Synopsis:**
```bash
aws identitystore update-user \
    --identity-store-id <value> \
    --user-id <value> \
    --operations <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-store-id` | **Yes** | string | -- | ID of the identity store |
| `--user-id` | **Yes** | string | -- | GUID of the user |
| `--operations` | **Yes** | list(structure) | -- | Update operations |

**Operations Structure:**
```json
[
    {
        "AttributePath": "string",
        "AttributeValue": "string|structure"
    }
]
```

Common attribute paths: `userName`, `name.givenName`, `name.familyName`, `displayName`, `emails`, `phoneNumbers`, `title`.

**Output Schema:**

No output on success (HTTP 200).

---

### 9.5 `get-user-id`

Looks up a user ID by an alternate identifier (e.g., username or external ID).

**Synopsis:**
```bash
aws identitystore get-user-id \
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
    "UserId": "string",
    "IdentityStoreId": "string"
}
```

---

### 9.6 `list-users`

Lists all users in the identity store. **Paginated operation.**

**Synopsis:**
```bash
aws identitystore list-users \
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
    "Users": [
        {
            "UserName": "string",
            "UserId": "string",
            "ExternalIds": [],
            "Name": {},
            "DisplayName": "string",
            "NickName": "string",
            "ProfileUrl": "string",
            "Emails": [],
            "Addresses": [],
            "PhoneNumbers": [],
            "UserType": "string",
            "Title": "string",
            "PreferredLanguage": "string",
            "Locale": "string",
            "Timezone": "string",
            "IdentityStoreId": "string"
        }
    ],
    "NextToken": "string"
}
```
