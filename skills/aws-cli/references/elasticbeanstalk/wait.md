# Wait

The `aws elasticbeanstalk wait` subcommand blocks until an environment reaches a specific state, polling every 20 seconds.

### 9.1 `wait environment-exists`

Wait until an environment exists. Polls `describe-environments` every 20 seconds until a successful response. Exits with return code 255 after 20 failed checks.

**Synopsis:**
```bash
aws elasticbeanstalk wait environment-exists \
    [--application-name <value>] \
    [--version-label <value>] \
    [--environment-ids <value>] \
    [--environment-names <value>] \
    [--include-deleted | --no-include-deleted] \
    [--included-deleted-back-to <value>] \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | No | string | -- | Application name |
| `--environment-ids` | No | list(string) | None | Environment IDs |
| `--environment-names` | No | list(string) | None | Environment names |

**Example:**
```bash
aws elasticbeanstalk wait environment-exists \
  --environment-names my-app-prod
```

---

### 9.2 `wait environment-terminated`

Wait until an environment is terminated. Polls `describe-environments` every 20 seconds until the environment status is `Terminated`. Exits with return code 255 after 20 failed checks.

**Synopsis:**
```bash
aws elasticbeanstalk wait environment-terminated \
    [--application-name <value>] \
    [--version-label <value>] \
    [--environment-ids <value>] \
    [--environment-names <value>] \
    [--include-deleted | --no-include-deleted] \
    [--included-deleted-back-to <value>] \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | No | string | -- | Application name |
| `--environment-ids` | No | list(string) | None | Environment IDs |
| `--environment-names` | No | list(string) | None | Environment names |

**Example:**
```bash
aws elasticbeanstalk terminate-environment --environment-name my-app-prod
aws elasticbeanstalk wait environment-terminated --environment-names my-app-prod
```

---

### 9.3 `wait environment-updated`

Wait until an environment is updated (status is `Ready`). Polls `describe-environments` every 20 seconds until the environment status is `Ready`. Exits with return code 255 after 20 failed checks.

**Synopsis:**
```bash
aws elasticbeanstalk wait environment-updated \
    [--application-name <value>] \
    [--version-label <value>] \
    [--environment-ids <value>] \
    [--environment-names <value>] \
    [--include-deleted | --no-include-deleted] \
    [--included-deleted-back-to <value>] \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | No | string | -- | Application name |
| `--environment-ids` | No | list(string) | None | Environment IDs |
| `--environment-names` | No | list(string) | None | Environment names |

**Example:**
```bash
aws elasticbeanstalk update-environment \
  --environment-name my-app-prod \
  --version-label v2.0.0
aws elasticbeanstalk wait environment-updated --environment-names my-app-prod
```
