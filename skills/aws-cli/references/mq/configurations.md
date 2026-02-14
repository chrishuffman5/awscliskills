# Configurations

### 2.1 `create-configuration`

Creates a broker configuration. ActiveMQ uses XML; RabbitMQ uses Cuttlefish format.

**Synopsis:**
```bash
aws mq create-configuration \
    --name <value> \
    --engine-type <value> \
    [--authentication-strategy <value>] \
    [--engine-version <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Configuration name (1-150 chars, alphanumeric, dashes, periods, underscores, tildes) |
| `--engine-type` | **Yes** | string | -- | `ACTIVEMQ` or `RABBITMQ` |
| `--authentication-strategy` | No | string | `SIMPLE` | `SIMPLE`, `LDAP`, `CONFIG_MANAGED` |
| `--engine-version` | No | string | Latest | Engine version |
| `--tags` | No | map | None | Resource tags |

**Output Schema:**
```json
{
    "Arn": "string",
    "AuthenticationStrategy": "SIMPLE|LDAP|CONFIG_MANAGED",
    "Created": "timestamp",
    "Id": "string",
    "LatestRevision": {
        "Created": "timestamp",
        "Description": "string",
        "Revision": integer
    },
    "Name": "string"
}
```

---

### 2.2 `describe-configuration`

Describes a broker configuration.

**Synopsis:**
```bash
aws mq describe-configuration \
    --configuration-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-id` | **Yes** | string | -- | The configuration ID |

**Output Schema:**
```json
{
    "Arn": "string",
    "AuthenticationStrategy": "SIMPLE|LDAP|CONFIG_MANAGED",
    "Created": "timestamp",
    "Description": "string",
    "EngineType": "ACTIVEMQ|RABBITMQ",
    "EngineVersion": "string",
    "Id": "string",
    "LatestRevision": {
        "Created": "timestamp",
        "Description": "string",
        "Revision": integer
    },
    "Name": "string",
    "Tags": {"string": "string"}
}
```

---

### 2.3 `list-configurations`

Lists all broker configurations. **Paginated operation.**

**Synopsis:**
```bash
aws mq list-configurations \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Configurations": [
        {
            "Arn": "string",
            "AuthenticationStrategy": "string",
            "Created": "timestamp",
            "Description": "string",
            "EngineType": "ACTIVEMQ|RABBITMQ",
            "EngineVersion": "string",
            "Id": "string",
            "LatestRevision": {
                "Created": "timestamp",
                "Description": "string",
                "Revision": integer
            },
            "Name": "string",
            "Tags": {}
        }
    ],
    "MaxResults": integer,
    "NextToken": "string"
}
```

---

### 2.4 `update-configuration`

Updates a configuration with new data. Creates a new revision.

**Synopsis:**
```bash
aws mq update-configuration \
    --configuration-id <value> \
    --data <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-id` | **Yes** | string | -- | The configuration ID |
| `--data` | **Yes** | string | -- | Base64-encoded configuration data (XML for ActiveMQ, Cuttlefish for RabbitMQ) |
| `--description` | No | string | None | Description of the revision |

**Output Schema:**
```json
{
    "Arn": "string",
    "Created": "timestamp",
    "Id": "string",
    "LatestRevision": {
        "Created": "timestamp",
        "Description": "string",
        "Revision": integer
    },
    "Name": "string",
    "Warnings": [
        {
            "AttributeName": "string",
            "ElementName": "string",
            "Reason": "DISALLOWED_ELEMENT_REMOVED|DISALLOWED_ATTRIBUTE_REMOVED|INVALID_ATTRIBUTE_VALUE_REMOVED"
        }
    ]
}
```

---

### 2.5 `delete-configuration`

Deletes a broker configuration. Cannot delete a configuration applied to any broker.

**Synopsis:**
```bash
aws mq delete-configuration \
    --configuration-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-id` | **Yes** | string | -- | The configuration ID to delete |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string"
}
```

---

### 2.6 `describe-configuration-revision`

Gets a specific configuration revision with its data.

**Synopsis:**
```bash
aws mq describe-configuration-revision \
    --configuration-id <value> \
    --configuration-revision <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-id` | **Yes** | string | -- | The configuration ID |
| `--configuration-revision` | **Yes** | string | -- | The revision number |

**Output Schema:**
```json
{
    "ConfigurationId": "string",
    "Created": "timestamp",
    "Data": "string",
    "Description": "string"
}
```

---

### 2.7 `list-configuration-revisions`

Lists revisions for a configuration. **Paginated operation.**

**Synopsis:**
```bash
aws mq list-configuration-revisions \
    --configuration-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-id` | **Yes** | string | -- | The configuration ID |
| `--max-results` | No | integer | None | Max results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ConfigurationId": "string",
    "MaxResults": integer,
    "NextToken": "string",
    "Revisions": [
        {
            "Created": "timestamp",
            "Description": "string",
            "Revision": integer
        }
    ]
}
```
