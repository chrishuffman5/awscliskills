# Domains

### 8.1 `create-domain`

Creates a domain resource for DNS management.

**Synopsis:**
```bash
aws lightsail create-domain \
    --domain-name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (e.g., `example.com`) |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Domain",
        "operationType": "CreateDomain",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 8.2 `delete-domain`

Deletes a domain resource and all associated DNS records.

**Synopsis:**
```bash
aws lightsail delete-domain \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name to delete |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Domain",
        "operationType": "DeleteDomain",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 8.3 `get-domain`

Returns information about a specific domain.

**Synopsis:**
```bash
aws lightsail get-domain \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |

**Output Schema:**
```json
{
    "domain": {
        "name": "string",
        "arn": "string",
        "supportCode": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "Domain",
        "tags": [],
        "domainEntries": [
            {
                "id": "string",
                "name": "string",
                "target": "string",
                "isAlias": true|false,
                "type": "string",
                "options": {}
            }
        ],
        "registeredDomainDelegationInfo": {
            "nameServersUpdateState": {
                "code": "SUCCEEDED|PENDING|FAILED|STARTED",
                "message": "string"
            },
            "r53HostedZoneDeletionState": {
                "code": "SUCCEEDED|PENDING|FAILED|STARTED",
                "message": "string"
            }
        }
    }
}
```

---

### 8.4 `get-domains`

Returns information about all domains. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-domains \
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
    "domains": [
        {
            "name": "string",
            "arn": "string",
            "resourceType": "Domain",
            "domainEntries": []
        }
    ],
    "nextPageToken": "string"
}
```

---

### 8.5 `create-domain-entry`

Creates a DNS record for a domain.

**Synopsis:**
```bash
aws lightsail create-domain-entry \
    --domain-name <value> \
    --domain-entry <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--domain-entry` | **Yes** | structure | -- | DNS entry. Shorthand: `name=string,target=string,type=A\|AAAA\|CNAME\|MX\|NS\|SOA\|SRV\|TXT,isAlias=boolean` |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Domain",
        "operationType": "CreateDomainEntry",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 8.6 `update-domain-entry`

Updates a DNS record for a domain.

**Synopsis:**
```bash
aws lightsail update-domain-entry \
    --domain-name <value> \
    --domain-entry <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--domain-entry` | **Yes** | structure | -- | Updated DNS entry. Shorthand: `id=string,name=string,target=string,type=string,isAlias=boolean` |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Domain",
            "operationType": "UpdateDomainEntry",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```

---

### 8.7 `delete-domain-entry`

Deletes a DNS record from a domain.

**Synopsis:**
```bash
aws lightsail delete-domain-entry \
    --domain-name <value> \
    --domain-entry <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--domain-entry` | **Yes** | structure | -- | DNS entry to delete. Shorthand: `id=string,name=string,target=string,type=string` |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "Domain",
        "operationType": "DeleteDomainEntry",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```
