# Wait

### 8.1 `wait workspace-active`

Polls `describe-workspace` every 2 seconds until the workspace status is `ACTIVE`. Exits with return code 255 after 60 failed checks.

**Synopsis:**
```bash
aws amp wait workspace-active \
    --workspace-id <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace to wait for |

**Output Schema:**
```json
{}
```

---

### 8.2 `wait workspace-deleted`

Polls `describe-workspace` every 2 seconds until the workspace is deleted (ResourceNotFoundException). Exits with return code 255 after 60 failed checks.

**Synopsis:**
```bash
aws amp wait workspace-deleted \
    --workspace-id <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace to wait for deletion |

**Output Schema:**
```json
{}
```

---

### 8.3 `wait scraper-active`

Polls `describe-scraper` every 2 seconds until the scraper status is `ACTIVE`. Exits with return code 255 after 60 failed checks.

**Synopsis:**
```bash
aws amp wait scraper-active \
    --scraper-id <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scraper-id` | **Yes** | string | -- | ID of the scraper to wait for |

**Output Schema:**
```json
{}
```

---

### 8.4 `wait scraper-deleted`

Polls `describe-scraper` every 2 seconds until the scraper is deleted (ResourceNotFoundException). Exits with return code 255 after 60 failed checks.

**Synopsis:**
```bash
aws amp wait scraper-deleted \
    --scraper-id <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scraper-id` | **Yes** | string | -- | ID of the scraper to wait for deletion |

**Output Schema:**
```json
{}
```
