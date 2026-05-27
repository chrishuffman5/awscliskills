# ID Mapping

## 8.1 `create-id-mapping-table`

Creates an ID mapping table within a membership.

**Synopsis:**
```bash
aws cleanrooms create-id-mapping-table \
    --membership-identifier <value> \
    --name <value> \
    --input-reference-config <value> \
    [--description <value>] \
    [--kms-key-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--name` | **Yes** | string | -- | ID mapping table name |
| `--input-reference-config` | **Yes** | structure | -- | Input reference configuration |
| `--description` | No | string | None | Description |
| `--kms-key-arn` | No | string | None | KMS key ARN for encryption |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "idMappingTable": {
        "id": "string",
        "arn": "string",
        "inputReferenceConfig": {},
        "membershipId": "string",
        "membershipArn": "string",
        "collaborationId": "string",
        "collaborationArn": "string",
        "description": "string",
        "name": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "inputReferenceProperties": {},
        "kmsKeyArn": "string"
    }
}
```

---

## 8.2 `delete-id-mapping-table`

Deletes an ID mapping table.

**Synopsis:**
```bash
aws cleanrooms delete-id-mapping-table \
    --membership-identifier <value> \
    --id-mapping-table-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--id-mapping-table-identifier` | **Yes** | string | -- | ID mapping table ID |

**Output Schema:**

None (HTTP 204 on success).

---

## 8.3 `get-id-mapping-table`

Returns details for an ID mapping table.

**Synopsis:**
```bash
aws cleanrooms get-id-mapping-table \
    --membership-identifier <value> \
    --id-mapping-table-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--id-mapping-table-identifier` | **Yes** | string | -- | ID mapping table ID |

**Output Schema:**
```json
{
    "idMappingTable": {
        "id": "string",
        "arn": "string",
        "inputReferenceConfig": {},
        "membershipId": "string",
        "collaborationId": "string",
        "name": "string",
        "description": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "inputReferenceProperties": {},
        "kmsKeyArn": "string"
    }
}
```

---

## 8.4 `list-id-mapping-tables`

Lists ID mapping tables for a membership. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-id-mapping-tables \
    --membership-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "idMappingTableSummaries": [
        {
            "collaborationArn": "string",
            "collaborationId": "string",
            "membershipId": "string",
            "membershipArn": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "id": "string",
            "arn": "string",
            "description": "string",
            "inputReferenceConfig": {},
            "name": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 8.5 `populate-id-mapping-table`

Populates an ID mapping table with data.

**Synopsis:**
```bash
aws cleanrooms populate-id-mapping-table \
    --membership-identifier <value> \
    --id-mapping-table-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--id-mapping-table-identifier` | **Yes** | string | -- | ID mapping table ID |

**Output Schema:**
```json
{
    "idMappingJobId": "string"
}
```

---

## 8.6 `update-id-mapping-table`

Updates an ID mapping table.

**Synopsis:**
```bash
aws cleanrooms update-id-mapping-table \
    --membership-identifier <value> \
    --id-mapping-table-identifier <value> \
    [--description <value>] \
    [--kms-key-arn <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--id-mapping-table-identifier` | **Yes** | string | -- | ID mapping table ID |
| `--description` | No | string | None | Updated description |
| `--kms-key-arn` | No | string | None | Updated KMS key ARN |

**Output Schema:**
```json
{
    "idMappingTable": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "updateTime": "timestamp"
    }
}
```

---

## 8.7 `create-id-namespace-association`

Creates an ID namespace association within a membership.

**Synopsis:**
```bash
aws cleanrooms create-id-namespace-association \
    --membership-identifier <value> \
    --input-reference-config <value> \
    --name <value> \
    [--description <value>] \
    [--id-mapping-config <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--input-reference-config` | **Yes** | structure | -- | Input reference configuration |
| `--name` | **Yes** | string | -- | Association name |
| `--description` | No | string | None | Description |
| `--id-mapping-config` | No | structure | None | ID mapping configuration |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "idNamespaceAssociation": {
        "id": "string",
        "arn": "string",
        "membershipId": "string",
        "membershipArn": "string",
        "collaborationId": "string",
        "collaborationArn": "string",
        "name": "string",
        "description": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "inputReferenceConfig": {},
        "inputReferenceProperties": {},
        "idMappingConfig": {}
    }
}
```

---

## 8.8-8.12 ID Namespace Association CRUD

`delete-id-namespace-association`, `get-id-namespace-association`, `list-id-namespace-associations`, and `update-id-namespace-association` follow standard CRUD patterns with `--membership-identifier` and `--id-namespace-association-identifier`.

`get-collaboration-id-namespace-association` and `list-collaboration-id-namespace-associations` provide collaboration-level views using `--collaboration-identifier`.

**Synopsis (list):**
```bash
aws cleanrooms list-id-namespace-associations \
    --membership-identifier <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```

**Synopsis (collaboration get):**
```bash
aws cleanrooms get-collaboration-id-namespace-association \
    --collaboration-identifier <value> \
    --id-namespace-association-identifier <value>
```

**Synopsis (collaboration list):**
```bash
aws cleanrooms list-collaboration-id-namespace-associations \
    --collaboration-identifier <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```
