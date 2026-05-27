# Source Credentials

### 6.1 `import-source-credentials`

Imports the source repository credentials for an AWS CodeBuild project that has its source code in a GitHub, GitHub Enterprise, GitLab, GitLab Self Managed, or Bitbucket repository.

**Synopsis:**
```bash
aws codebuild import-source-credentials \
    --server-type <value> \
    --auth-type <value> \
    --token <value> \
    [--username <value>] \
    [--should-overwrite | --no-should-overwrite] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--server-type` | **Yes** | string | -- | Source provider: `GITHUB`, `BITBUCKET`, `GITHUB_ENTERPRISE`, `GITLAB`, `GITLAB_SELF_MANAGED` |
| `--auth-type` | **Yes** | string | -- | Auth type: `OAUTH`, `BASIC_AUTH`, `PERSONAL_ACCESS_TOKEN`, `CODECONNECTIONS` |
| `--token` | **Yes** | string | -- | Access token or connection ARN |
| `--username` | No | string | None | Bitbucket username (required for Bitbucket with BASIC_AUTH) |
| `--should-overwrite` | No | boolean | false | Overwrite existing credentials for this server type |

**Output Schema:**
```json
{
    "arn": "string"
}
```

---

### 6.2 `delete-source-credentials`

Deletes a set of GitHub, GitHub Enterprise, GitLab, GitLab Self Managed, or Bitbucket source credentials.

**Synopsis:**
```bash
aws codebuild delete-source-credentials \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Source credentials ARN |

**Output Schema:**
```json
{
    "arn": "string"
}
```

---

### 6.3 `list-source-credentials`

Returns a list of source code credentials for your account.

**Synopsis:**
```bash
aws codebuild list-source-credentials \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No additional parameters.

**Output Schema:**
```json
{
    "sourceCredentialsInfos": [
        {
            "arn": "string",
            "serverType": "GITHUB|BITBUCKET|GITHUB_ENTERPRISE|GITLAB|GITLAB_SELF_MANAGED",
            "authType": "OAUTH|BASIC_AUTH|PERSONAL_ACCESS_TOKEN|CODECONNECTIONS",
            "resource": "string"
        }
    ]
}
```
