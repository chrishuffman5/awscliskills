# Access & API

### 2.1 `create-cli-token`

Creates a CLI token to authenticate Airflow CLI commands against an Amazon MWAA environment.

**Synopsis:**
```bash
aws mwaa create-cli-token \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name (1-80 chars) |

**Output Schema:**
```json
{
    "CliToken": "string",
    "WebServerHostname": "string"
}
```

**Usage Example:**
```bash
# Get token and hostname, then run an Airflow CLI command
CLI_TOKEN=$(aws mwaa create-cli-token --name my-env --query CliToken --output text)
HOSTNAME=$(aws mwaa create-cli-token --name my-env --query WebServerHostname --output text)

curl -s "https://$HOSTNAME/aws_mwaa/cli" \
  -H "Authorization: Bearer $CLI_TOKEN" \
  -H "Content-Type: text/plain" \
  -d "dags list"
```

---

### 2.2 `create-web-login-token`

Creates a web login token for accessing the Apache Airflow UI.

**Synopsis:**
```bash
aws mwaa create-web-login-token \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name (1-80 chars) |

**Output Schema:**
```json
{
    "WebToken": "string",
    "WebServerHostname": "string",
    "AirflowIdentity": "string"
}
```

**Usage Example:**
```bash
# Generate a login URL for the Airflow web UI
TOKEN=$(aws mwaa create-web-login-token --name my-env --query WebToken --output text)
HOST=$(aws mwaa create-web-login-token --name my-env --query WebServerHostname --output text)
echo "https://$HOST/aws_mwaa/aws-console-sso?login=true#$TOKEN"
```

---

### 2.3 `invoke-rest-api`

Invokes the Apache Airflow REST API on the environment. Allows programmatic interaction with Airflow DAGs, tasks, and other resources.

**Synopsis:**
```bash
aws mwaa invoke-rest-api \
    --name <value> \
    --path <value> \
    --method <value> \
    [--query-parameters <value>] \
    [--body <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name (1-80 chars) |
| `--path` | **Yes** | string | -- | Airflow REST API endpoint path (e.g., `/dags`, `/dags/{dag_id}/dagRuns`) |
| `--method` | **Yes** | string | -- | HTTP method: `GET`, `PUT`, `POST`, `PATCH`, `DELETE` |
| `--query-parameters` | No | document | None | Query parameters as a JSON object |
| `--body` | No | document | None | Request body as a JSON object |

**Output Schema:**
```json
{
    "RestApiStatusCode": "integer",
    "RestApiResponse": "document"
}
```

**Usage Examples:**
```bash
# List all DAGs
aws mwaa invoke-rest-api --name my-env --path "/dags" --method GET

# Trigger a DAG run
aws mwaa invoke-rest-api --name my-env \
  --path "/dags/my_dag/dagRuns" --method POST \
  --body '{"conf": {"key": "value"}}'

# Get task instances for a DAG run
aws mwaa invoke-rest-api --name my-env \
  --path "/dags/my_dag/dagRuns/run_id/taskInstances" --method GET

# Pause a DAG
aws mwaa invoke-rest-api --name my-env \
  --path "/dags/my_dag" --method PATCH \
  --body '{"is_paused": true}'
```

---

### 2.4 `tag-resource`

Adds tags to an Amazon MWAA resource.

**Synopsis:**
```bash
aws mwaa tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the MWAA resource |
| `--tags` | **Yes** | map | -- | Key-value tag pairs to add |

**Output Schema:**
```json
{}
```

---

### 2.5 `untag-resource`

Removes tags from an Amazon MWAA resource.

**Synopsis:**
```bash
aws mwaa untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the MWAA resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{}
```

---

### 2.6 `list-tags-for-resource`

Lists tags for an Amazon MWAA resource.

**Synopsis:**
```bash
aws mwaa list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the MWAA resource |

**Output Schema:**
```json
{
    "Tags": {
        "key": "string"
    }
}
```
