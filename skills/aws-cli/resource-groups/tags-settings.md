# Tags & Settings

### 4.1 `tag`

Adds tags to a resource group. Unlike `tag-resource` in other services, this command uses the resource group ARN as the positional argument.

**Synopsis:**
```bash
aws resource-groups tag \
    --arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource group to tag |
| `--tags` | **Yes** | map | -- | Tags to add. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "Arn": "string",
    "Tags": {
        "string": "string"
    }
}
```

---

### 4.2 `untag`

Removes tags from a resource group.

**Synopsis:**
```bash
aws resource-groups untag \
    --arn <value> \
    --keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource group to untag |
| `--keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{
    "Arn": "string",
    "Keys": ["string"]
}
```

---

### 4.3 `get-tags`

Returns a list of tags associated with a resource group.

**Synopsis:**
```bash
aws resource-groups get-tags \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the resource group |

**Output Schema:**
```json
{
    "Arn": "string",
    "Tags": {
        "string": "string"
    }
}
```

---

### 4.4 `get-account-settings`

Retrieves the current status of optional features in Resource Groups.

**Synopsis:**
```bash
aws resource-groups get-account-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| -- | -- | -- | -- | No required parameters |

**Output Schema:**
```json
{
    "AccountSettings": {
        "GroupLifecycleEventsDesiredStatus": "ACTIVE|INACTIVE",
        "GroupLifecycleEventsStatus": "ACTIVE|INACTIVE|IN_PROGRESS|ERROR",
        "GroupLifecycleEventsStatusMessage": "string"
    }
}
```

---

### 4.5 `update-account-settings`

Turns on or turns off optional features in Resource Groups.

**Synopsis:**
```bash
aws resource-groups update-account-settings \
    [--group-lifecycle-events-desired-status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-lifecycle-events-desired-status` | No | string | None | Desired status: `ACTIVE` or `INACTIVE` |

**Output Schema:**
```json
{
    "AccountSettings": {
        "GroupLifecycleEventsDesiredStatus": "ACTIVE|INACTIVE",
        "GroupLifecycleEventsStatus": "ACTIVE|INACTIVE|IN_PROGRESS|ERROR",
        "GroupLifecycleEventsStatusMessage": "string"
    }
}
```
