# Contact Lists

### 3.1 `create-contact-list`

Creates a contact list for managing subscription preferences and topics.

**Synopsis:**
```bash
aws sesv2 create-contact-list \
    --contact-list-name <value> \
    [--topics <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-list-name` | **Yes** | string | -- | Name of the contact list |
| `--topics` | No | list | None | Topics for subscription management |
| `--description` | No | string | None | Description of the contact list |
| `--tags` | No | list | None | Tags to apply. Shorthand: `Key=string,Value=string ...` |

**Topic Structure:**
```json
[
    {
        "TopicName": "string",
        "DisplayName": "string",
        "Description": "string",
        "DefaultSubscriptionStatus": "OPT_IN|OPT_OUT"
    }
]
```

**Output Schema:**
```json
{}
```

---

### 3.2 `delete-contact-list`

Deletes a contact list and all contacts within it.

**Synopsis:**
```bash
aws sesv2 delete-contact-list \
    --contact-list-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-list-name` | **Yes** | string | -- | Name of the contact list to delete |

**Output Schema:**
```json
{}
```

---

### 3.3 `get-contact-list`

Returns information about a contact list.

**Synopsis:**
```bash
aws sesv2 get-contact-list \
    --contact-list-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-list-name` | **Yes** | string | -- | Name of the contact list |

**Output Schema:**
```json
{
    "ContactListName": "string",
    "Topics": [
        {
            "TopicName": "string",
            "DisplayName": "string",
            "Description": "string",
            "DefaultSubscriptionStatus": "OPT_IN|OPT_OUT"
        }
    ],
    "Description": "string",
    "CreatedTimestamp": "timestamp",
    "LastUpdatedTimestamp": "timestamp",
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 3.4 `list-contact-lists`

Lists all contact lists in the account. **Paginated operation.**

**Synopsis:**
```bash
aws sesv2 list-contact-lists \
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
    "ContactLists": [
        {
            "ContactListName": "string",
            "LastUpdatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `update-contact-list`

Updates a contact list's topics and description.

**Synopsis:**
```bash
aws sesv2 update-contact-list \
    --contact-list-name <value> \
    [--topics <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-list-name` | **Yes** | string | -- | Name of the contact list to update |
| `--topics` | No | list | None | Updated topics (same structure as create) |
| `--description` | No | string | None | Updated description |

**Output Schema:**
```json
{}
```

---

### 3.6 `create-contact`

Creates a contact in a contact list with optional topic preferences.

**Synopsis:**
```bash
aws sesv2 create-contact \
    --contact-list-name <value> \
    --email-address <value> \
    [--topic-preferences <value>] \
    [--unsubscribe-all | --no-unsubscribe-all] \
    [--attributes-data <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-list-name` | **Yes** | string | -- | Contact list to add the contact to |
| `--email-address` | **Yes** | string | -- | Contact email address |
| `--topic-preferences` | No | list | None | Topic subscription preferences |
| `--unsubscribe-all` | No | boolean | false | Unsubscribe contact from all topics |
| `--attributes-data` | No | string | None | JSON string of attribute data for the contact |

**Topic Preferences Structure:**
```json
[
    {
        "TopicName": "string",
        "SubscriptionStatus": "OPT_IN|OPT_OUT"
    }
]
```

**Output Schema:**
```json
{}
```

---

### 3.7 `delete-contact`

Removes a contact from a contact list.

**Synopsis:**
```bash
aws sesv2 delete-contact \
    --contact-list-name <value> \
    --email-address <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-list-name` | **Yes** | string | -- | Contact list name |
| `--email-address` | **Yes** | string | -- | Email address of the contact to remove |

**Output Schema:**
```json
{}
```

---

### 3.8 `get-contact`

Returns information about a specific contact in a contact list.

**Synopsis:**
```bash
aws sesv2 get-contact \
    --contact-list-name <value> \
    --email-address <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-list-name` | **Yes** | string | -- | Contact list name |
| `--email-address` | **Yes** | string | -- | Email address of the contact |

**Output Schema:**
```json
{
    "ContactListName": "string",
    "EmailAddress": "string",
    "TopicPreferences": [
        {
            "TopicName": "string",
            "SubscriptionStatus": "OPT_IN|OPT_OUT"
        }
    ],
    "TopicDefaultPreferences": [
        {
            "TopicName": "string",
            "SubscriptionStatus": "OPT_IN|OPT_OUT"
        }
    ],
    "UnsubscribeAll": true|false,
    "AttributesData": "string",
    "CreatedTimestamp": "timestamp",
    "LastUpdatedTimestamp": "timestamp"
}
```

---

### 3.9 `list-contacts`

Lists contacts in a contact list. Supports filtering by topic preferences. **Paginated operation.**

**Synopsis:**
```bash
aws sesv2 list-contacts \
    --contact-list-name <value> \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-list-name` | **Yes** | string | -- | Contact list name |
| `--filter` | No | structure | None | Filter contacts by topic subscription status |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
{
    "FilteredStatus": "OPT_IN|OPT_OUT",
    "TopicFilter": {
        "TopicName": "string",
        "UseDefaultIfPreferenceUnavailable": true|false
    }
}
```

**Output Schema:**
```json
{
    "Contacts": [
        {
            "EmailAddress": "string",
            "TopicPreferences": [
                {
                    "TopicName": "string",
                    "SubscriptionStatus": "OPT_IN|OPT_OUT"
                }
            ],
            "TopicDefaultPreferences": [],
            "UnsubscribeAll": true|false,
            "LastUpdatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.10 `update-contact`

Updates a contact's subscription preferences in a contact list.

**Synopsis:**
```bash
aws sesv2 update-contact \
    --contact-list-name <value> \
    --email-address <value> \
    [--topic-preferences <value>] \
    [--unsubscribe-all | --no-unsubscribe-all] \
    [--attributes-data <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-list-name` | **Yes** | string | -- | Contact list name |
| `--email-address` | **Yes** | string | -- | Email address of the contact to update |
| `--topic-preferences` | No | list | None | Updated topic preferences |
| `--unsubscribe-all` | No | boolean | -- | Unsubscribe from all topics |
| `--attributes-data` | No | string | None | Updated JSON attribute data |

**Output Schema:**
```json
{}
```
