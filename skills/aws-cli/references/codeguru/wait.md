# Wait Commands

The `aws codeguru-reviewer wait` subcommand blocks until a resource reaches a specific state. It polls every few seconds until success or a maximum number of attempts is reached.

### 8.1 `wait code-review-completed`

Waits until a code review has reached the `Completed` state. Polls `describe-code-review` every 10 seconds until the state is `Completed`. Exits with a return code of 255 after 180 failed checks (30 minutes).

**Synopsis:**
```bash
aws codeguru-reviewer wait code-review-completed \
    --code-review-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-review-arn` | **Yes** | string | -- | ARN of the code review to wait for |

**Output Schema:**
```json
{}
```

No output on success. Returns exit code 0 when the code review reaches the `Completed` state. Returns exit code 255 if the waiter times out.

---

### 8.2 `wait repository-association-succeeded`

Waits until a repository association has reached the `Associated` state. Polls `describe-repository-association` every 10 seconds until the state is `Associated`. Exits with a return code of 255 after 30 failed checks (5 minutes).

**Synopsis:**
```bash
aws codeguru-reviewer wait repository-association-succeeded \
    --association-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-arn` | **Yes** | string | -- | ARN of the repository association to wait for |

**Output Schema:**
```json
{}
```

No output on success. Returns exit code 0 when the repository association reaches the `Associated` state. Returns exit code 255 if the waiter times out.
