# Revisions

### 5.1 `register-application-revision`

Registers with CodeDeploy a revision for the specified application.

**Synopsis:**
```bash
aws deploy register-application-revision \
    --application-name <value> \
    [--description <value>] \
    [--revision <value>] \
    [--s3-location <value>] \
    [--github-location <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--description` | No | string | None | Revision description |
| `--revision` | No | structure | None | Full revision location |
| `--s3-location` | No | structure | None | S3 revision location. Shorthand: `bucket=string,key=string,bundleType=tar\|tgz\|zip\|YAML\|JSON,version=string,eTag=string` |
| `--github-location` | No | structure | None | GitHub revision location. Shorthand: `repository=string,commitId=string` |

**Output Schema:**
```json
{}
```

---

### 5.2 `get-application-revision`

Gets information about an application revision.

**Synopsis:**
```bash
aws deploy get-application-revision \
    --application-name <value> \
    --revision <value> \
    [--s3-location <value>] \
    [--github-location <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--revision` | **Yes** | structure | -- | Revision location |
| `--s3-location` | No | structure | None | S3 revision location (shorthand alternative) |
| `--github-location` | No | structure | None | GitHub revision location (shorthand alternative) |

**Output Schema:**
```json
{
    "applicationName": "string",
    "revision": {
        "revisionType": "S3|GitHub|String|AppSpecContent",
        "s3Location": {
            "bucket": "string",
            "key": "string",
            "bundleType": "tar|tgz|zip|YAML|JSON",
            "version": "string",
            "eTag": "string"
        },
        "gitHubLocation": {
            "repository": "string",
            "commitId": "string"
        },
        "string": {
            "content": "string",
            "sha256": "string"
        },
        "appSpecContent": {
            "content": "string",
            "sha256": "string"
        }
    },
    "revisionInfo": {
        "description": "string",
        "deploymentGroups": ["string"],
        "firstUsedTime": "timestamp",
        "lastUsedTime": "timestamp",
        "registerTime": "timestamp"
    }
}
```

---

### 5.3 `list-application-revisions`

Lists information about revisions for an application. **Paginated operation.**

**Synopsis:**
```bash
aws deploy list-application-revisions \
    --application-name <value> \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--s3-bucket <value>] \
    [--s3-key-prefix <value>] \
    [--deployed <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--sort-by` | No | string | None | Sort criterion: `registerTime`, `firstUsedTime`, `lastUsedTime` |
| `--sort-order` | No | string | None | Sort order: `ascending`, `descending` |
| `--s3-bucket` | No | string | None | S3 bucket name filter |
| `--s3-key-prefix` | No | string | None | S3 key prefix filter |
| `--deployed` | No | string | None | Filter by deployment status: `include`, `exclude`, `ignore` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "revisions": [
        {
            "revisionType": "S3|GitHub|String|AppSpecContent",
            "s3Location": { },
            "gitHubLocation": { },
            "string": { },
            "appSpecContent": { }
        }
    ],
    "nextToken": "string"
}
```

---

### 5.4 `batch-get-application-revisions`

Gets information about one or more application revisions.

**Synopsis:**
```bash
aws deploy batch-get-application-revisions \
    --application-name <value> \
    --revisions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name |
| `--revisions` | **Yes** | list | -- | List of revision locations |

**Output Schema:**
```json
{
    "applicationName": "string",
    "errorMessage": "string",
    "revisions": [
        {
            "revisionLocation": {
                "revisionType": "S3|GitHub|String|AppSpecContent",
                "s3Location": { },
                "gitHubLocation": { }
            },
            "genericRevisionInfo": {
                "description": "string",
                "deploymentGroups": ["string"],
                "firstUsedTime": "timestamp",
                "lastUsedTime": "timestamp",
                "registerTime": "timestamp"
            }
        }
    ]
}
```
