# Opt-In

### 5.1 `create-lake-formation-opt-in`

Opts in a principal to Lake Formation permissions for a specific resource. When opted in, access to the resource is governed by Lake Formation permissions rather than IAM policies alone.

**Synopsis:**
```bash
aws lakeformation create-lake-formation-opt-in \
    --principal <value> \
    --resource <value> \
    [--condition <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--principal` | **Yes** | structure | -- | The principal to opt in. `{"DataLakePrincipalIdentifier":"arn:aws:iam::..."}` |
| `--resource` | **Yes** | structure | -- | The resource (Database, Table, etc.) |
| `--condition` | No | structure | None | Cedar Policy Language condition |

**Output:** None

---

### 5.2 `delete-lake-formation-opt-in`

Removes a Lake Formation opt-in for a principal on a resource.

**Synopsis:**
```bash
aws lakeformation delete-lake-formation-opt-in \
    --principal <value> \
    --resource <value> \
    [--condition <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--principal` | **Yes** | structure | -- | The principal to remove opt-in for |
| `--resource` | **Yes** | structure | -- | The resource |
| `--condition` | No | structure | None | Cedar Policy Language condition |

**Output:** None

---

### 5.3 `list-lake-formation-opt-ins`

Lists Lake Formation opt-ins. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation list-lake-formation-opt-ins \
    [--principal <value>] \
    [--resource <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--principal` | No | structure | None | Filter by principal |
| `--resource` | No | structure | None | Filter by resource |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Output Schema:**
```json
{
    "LakeFormationOptInsInfoList": [
        {
            "Resource": {},
            "Principal": {
                "DataLakePrincipalIdentifier": "string"
            },
            "Condition": {
                "Expression": "string"
            },
            "LastModified": "timestamp",
            "LastUpdatedBy": "string"
        }
    ],
    "NextToken": "string"
}
```
