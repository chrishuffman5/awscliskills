# Contacts & Tags

### 14.1 `create-contact-method`

Creates a contact method (email or SMS) for alarm notifications.

**Synopsis:**
```bash
aws lightsail create-contact-method \
    --protocol <value> \
    --contact-endpoint <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protocol` | **Yes** | string | -- | Protocol: `Email`, `SMS` |
| `--contact-endpoint` | **Yes** | string | -- | Contact endpoint (email address or phone number) |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "ContactMethod",
            "operationType": "CreateContactMethod",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 14.2 `delete-contact-method`

Deletes a contact method.

**Synopsis:**
```bash
aws lightsail delete-contact-method \
    --protocol <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protocol` | **Yes** | string | -- | Protocol of the contact method to delete: `Email`, `SMS` |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "ContactMethod",
            "operationType": "DeleteContactMethod",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 14.3 `get-contact-methods`

Returns information about contact methods.

**Synopsis:**
```bash
aws lightsail get-contact-methods \
    [--protocols <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protocols` | No | list(string) | None | Filter by protocol: `Email`, `SMS` |

**Output Schema:**
```json
{
    "contactMethods": [
        {
            "contactEndpoint": "string",
            "status": "PendingVerification|Valid|InValid",
            "protocol": "Email|SMS",
            "name": "string",
            "arn": "string",
            "createdAt": "timestamp",
            "location": {
                "availabilityZone": "string",
                "regionName": "string"
            },
            "resourceType": "ContactMethod",
            "supportCode": "string"
        }
    ]
}
```

---

### 14.4 `send-contact-method-verification`

Sends a verification request for a contact method.

**Synopsis:**
```bash
aws lightsail send-contact-method-verification \
    --protocol <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protocol` | **Yes** | string | -- | Protocol: `Email` |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "ContactMethod",
            "operationType": "SendContactMethodVerification",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 14.5 `tag-resource`

Adds tags to a Lightsail resource.

**Synopsis:**
```bash
aws lightsail tag-resource \
    --resource-name <value> \
    --tags <value> \
    [--resource-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | Name of the resource |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `key=string,value=string ...` |
| `--resource-arn` | No | string | None | ARN of the resource |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "string",
            "operationType": "TagResource",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 14.6 `untag-resource`

Removes tags from a Lightsail resource.

**Synopsis:**
```bash
aws lightsail untag-resource \
    --resource-name <value> \
    --tag-keys <value> \
    [--resource-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | Name of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |
| `--resource-arn` | No | string | None | ARN of the resource |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "string",
            "operationType": "UntagResource",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 14.7 `get-cost-estimate`

Returns the estimated monthly cost for a resource.

**Synopsis:**
```bash
aws lightsail get-cost-estimate \
    --resource-name <value> \
    --start-time <value> \
    --end-time <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | Name of the resource |
| `--start-time` | **Yes** | timestamp | -- | Start of the cost estimate period |
| `--end-time` | **Yes** | timestamp | -- | End of the cost estimate period |

**Output Schema:**
```json
{
    "resourcesBudgetEstimate": [
        {
            "resourceName": "string",
            "resourceType": "string",
            "costEstimates": [
                {
                    "usageType": "string",
                    "resultsByTime": [
                        {
                            "usageCost": "double",
                            "pricingUnit": "string",
                            "unit": "double",
                            "currency": "string",
                            "timePeriod": {
                                "start": "timestamp",
                                "end": "timestamp"
                            }
                        }
                    ]
                }
            ],
            "startTime": "timestamp",
            "endTime": "timestamp"
        }
    ]
}
```

---

### 14.8 `get-active-names`

Returns a list of active resource names. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-active-names \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "activeNames": ["string"],
    "nextPageToken": "string"
}
```

---

### 14.9 `get-operation`

Returns information about a specific operation.

**Synopsis:**
```bash
aws lightsail get-operation \
    --operation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--operation-id` | **Yes** | string | -- | ID of the operation |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "isTerminal": true|false,
        "operationDetails": "string",
        "operationType": "string",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "statusChangedAt": "timestamp",
        "errorCode": "string",
        "errorDetails": "string"
    }
}
```

---

### 14.10 `get-operations`

Returns information about all operations. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-operations \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "string",
            "operationType": "string",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false,
            "createdAt": "timestamp"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 14.11 `get-operations-for-resource`

Returns operations for a specific resource. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-operations-for-resource \
    --resource-name <value> \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | Name of the resource |
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "string",
            "operationType": "string",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false,
            "createdAt": "timestamp"
        }
    ],
    "nextPageCount": "string",
    "nextPageToken": "string"
}
```
