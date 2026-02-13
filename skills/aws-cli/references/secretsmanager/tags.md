# Tags

### 8.1 `tag-resource`

Adds tags to a secret. Tags are appended to the existing tag list, not replaced.

**Synopsis:**
```bash
aws secretsmanager tag-resource \
    --secret-id <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` or JSON: `[{"Key":"k","Value":"v"}]`. Key max 128, Value max 256 chars |

**Output Schema:**

None (no output on success).

---

### 8.2 `untag-resource`

Removes tags from a secret by tag key names.

**Synopsis:**
```bash
aws secretsmanager untag-resource \
    --secret-id <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |
| `--tag-keys` | **Yes** | list(string) | -- | Tag key names to remove (each 1-128 chars) |

**Output Schema:**

None (no output on success).

---
