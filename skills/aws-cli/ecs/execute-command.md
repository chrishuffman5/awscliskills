# Execute Command

### 12.1 `execute-command`

Runs a command remotely in a container. Requires the ECS Exec feature to be enabled on the service or task. Requires the Session Manager plugin for the AWS CLI.

**Synopsis:**
```bash
aws ecs execute-command \
    --task <value> \
    --command <value> \
    --interactive \
    [--cluster <value>] \
    [--container <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task` | **Yes** | string | -- | Task ID or full ARN |
| `--command` | **Yes** | string | -- | Command to run on the container |
| `--interactive` / `--non-interactive` | **Yes** | boolean | -- | Run in interactive mode (required for shell access) |
| `--cluster` | No | string | `default` | Cluster short name or ARN |
| `--container` | No | string | None | Container name (required for multi-container tasks) |

**Output:** Opens an interactive session. No JSON output.

> **Prerequisites:** Enable execute command on the service: `aws ecs update-service --cluster my-cluster --service my-service --enable-execute-command`. The task role must have `ssmmessages:CreateControlChannel`, `ssmmessages:CreateDataChannel`, `ssmmessages:OpenControlChannel`, `ssmmessages:OpenDataChannel` permissions.
