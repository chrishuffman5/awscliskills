# IP Groups

### 4.1 `create-ip-group`

Creates an IP access control group. An IP access control group provides you with the ability to control the IP addresses from which users are allowed to access their WorkSpaces.

**Synopsis:**
```bash
aws workspaces create-ip-group \
    --group-name <value> \
    [--group-desc <value>] \
    [--user-rules <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | **Yes** | string | -- | The name of the group |
| `--group-desc` | No | string | None | The description of the group |
| `--user-rules` | No | list | None | IP rules. Shorthand: `ipRule=string,ruleDesc=string ...` |
| `--tags` | No | list | None | Tags to associate. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "GroupId": "string"
}
```

---

### 4.2 `delete-ip-group`

Deletes the specified IP access control group.

**Synopsis:**
```bash
aws workspaces delete-ip-group \
    --group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-id` | **Yes** | string | -- | The group ID to delete |

**Output Schema:**
```json
{}
```

---

### 4.3 `describe-ip-groups`

Describes the specified IP access control groups or all groups. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces describe-ip-groups \
    [--group-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-ids` | No | list(string) | None | One or more group IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Result": [
        {
            "groupId": "string",
            "groupName": "string",
            "groupDesc": "string",
            "userRules": [
                {
                    "ipRule": "string",
                    "ruleDesc": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `authorize-ip-rules`

Adds one or more rules to the specified IP access control group.

**Synopsis:**
```bash
aws workspaces authorize-ip-rules \
    --group-id <value> \
    --user-rules <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-id` | **Yes** | string | -- | The group ID |
| `--user-rules` | **Yes** | list | -- | IP rules to add. Shorthand: `ipRule=string,ruleDesc=string ...` |

**Output Schema:**
```json
{}
```

---

### 4.5 `revoke-ip-rules`

Removes one or more rules from the specified IP access control group.

**Synopsis:**
```bash
aws workspaces revoke-ip-rules \
    --group-id <value> \
    --user-rules <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-id` | **Yes** | string | -- | The group ID |
| `--user-rules` | **Yes** | list(string) | -- | IP rules (CIDR ranges) to remove |

**Output Schema:**
```json
{}
```

---

### 4.6 `update-rules-of-ip-group`

Replaces the current rules of the specified IP access control group with the specified rules.

**Synopsis:**
```bash
aws workspaces update-rules-of-ip-group \
    --group-id <value> \
    --user-rules <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-id` | **Yes** | string | -- | The group ID |
| `--user-rules` | **Yes** | list | -- | Replacement IP rules. Shorthand: `ipRule=string,ruleDesc=string ...` |

**Output Schema:**
```json
{}
```

---

### 4.7 `associate-ip-groups`

Associates the specified IP access control groups with the specified directory.

**Synopsis:**
```bash
aws workspaces associate-ip-groups \
    --directory-id <value> \
    --group-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | The directory ID |
| `--group-ids` | **Yes** | list(string) | -- | One or more IP access control group IDs |

**Output Schema:**
```json
{}
```

---

### 4.8 `disassociate-ip-groups`

Disassociates the specified IP access control groups from the specified directory.

**Synopsis:**
```bash
aws workspaces disassociate-ip-groups \
    --directory-id <value> \
    --group-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | The directory ID |
| `--group-ids` | **Yes** | list(string) | -- | One or more IP access control group IDs |

**Output Schema:**
```json
{}
```
