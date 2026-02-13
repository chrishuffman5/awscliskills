# Triggers

### 8.1 `get-repository-triggers`

Returns information about triggers configured for a repository.

**Synopsis:**
```bash
aws codecommit get-repository-triggers \
    --repository-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |

**Output Schema:**
```json
{
    "configurationId": "string",
    "triggers": [
        {
            "name": "string",
            "destinationArn": "string",
            "customData": "string",
            "branches": ["string"],
            "events": ["all|updateReference|createReference|deleteReference"]
        }
    ]
}
```

---

### 8.2 `put-repository-triggers`

Replaces all triggers for a repository. Used to create, update, or delete triggers.

**Synopsis:**
```bash
aws codecommit put-repository-triggers \
    --repository-name <value> \
    --triggers <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--triggers` | **Yes** | list | -- | Triggers to configure. JSON: `[{"name":"string","destinationArn":"string","customData":"string","branches":["string"],"events":["all\|updateReference\|createReference\|deleteReference"]}]` |

**Output Schema:**
```json
{
    "configurationId": "string"
}
```

---

### 8.3 `test-repository-triggers`

Tests the functionality of repository triggers by sending information to the trigger target.

**Synopsis:**
```bash
aws codecommit test-repository-triggers \
    --repository-name <value> \
    --triggers <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--triggers` | **Yes** | list | -- | Triggers to test (same format as put-repository-triggers) |

**Output Schema:**
```json
{
    "successfulExecutions": ["string"],
    "failedExecutions": [
        {
            "trigger": "string",
            "failureMessage": "string"
        }
    ]
}
```
