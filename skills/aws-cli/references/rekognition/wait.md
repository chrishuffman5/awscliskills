# Wait

The `aws rekognition wait` subcommand blocks until a resource reaches a specific state, polling every few seconds.

---

### 11.1 `wait project-version-running`

Waits until a project version (model) is running. Polls `describe-project-versions` every 30 seconds until the status is `RUNNING`. Exits with return code 255 after 40 failed checks.

**Synopsis:**
```bash
aws rekognition wait project-version-running \
    --project-arn <value> \
    [--version-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the project |
| `--version-names` | No | list(string) | -- | Filter by version names (1-10) |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output:** None (exits when condition is met or max attempts exceeded)

---

### 11.2 `wait project-version-training-completed`

Waits until a project version training is completed. Polls `describe-project-versions` every 120 seconds until the status is `TRAINING_COMPLETED`. Exits with return code 255 after 360 failed checks.

**Synopsis:**
```bash
aws rekognition wait project-version-training-completed \
    --project-arn <value> \
    [--version-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the project |
| `--version-names` | No | list(string) | -- | Filter by version names (1-10) |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output:** None (exits when condition is met or max attempts exceeded)
