# Audience Model Associations

## 9.1 `create-configured-audience-model-association`

Associates a configured audience model with a membership in a collaboration.

**Synopsis:**
```bash
aws cleanrooms create-configured-audience-model-association \
    --membership-identifier <value> \
    --configured-audience-model-arn <value> \
    --configured-audience-model-association-name <value> \
    --manage-resource-policies <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--configured-audience-model-arn` | **Yes** | string | -- | Configured audience model ARN |
| `--configured-audience-model-association-name` | **Yes** | string | -- | Association name |
| `--manage-resource-policies` | **Yes** | boolean | -- | Whether to manage resource policies |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "configuredAudienceModelAssociation": {
        "id": "string",
        "arn": "string",
        "configuredAudienceModelArn": "string",
        "membershipId": "string",
        "membershipArn": "string",
        "collaborationId": "string",
        "collaborationArn": "string",
        "name": "string",
        "manageResourcePolicies": "boolean",
        "description": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

## 9.2 `delete-configured-audience-model-association`

Deletes a configured audience model association.

**Synopsis:**
```bash
aws cleanrooms delete-configured-audience-model-association \
    --membership-identifier <value> \
    --configured-audience-model-association-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--configured-audience-model-association-identifier` | **Yes** | string | -- | Association ID |

**Output Schema:**

None (HTTP 204 on success).

---

## 9.3 `get-configured-audience-model-association`

Returns details for an audience model association.

**Synopsis:**
```bash
aws cleanrooms get-configured-audience-model-association \
    --membership-identifier <value> \
    --configured-audience-model-association-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--configured-audience-model-association-identifier` | **Yes** | string | -- | Association ID |

**Output Schema:**
```json
{
    "configuredAudienceModelAssociation": {
        "id": "string",
        "arn": "string",
        "configuredAudienceModelArn": "string",
        "membershipId": "string",
        "collaborationId": "string",
        "name": "string",
        "description": "string",
        "manageResourcePolicies": "boolean",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

## 9.4 `list-configured-audience-model-associations`

Lists audience model associations for a membership. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-configured-audience-model-associations \
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
    "configuredAudienceModelAssociationSummaries": [
        {
            "membershipId": "string",
            "membershipArn": "string",
            "collaborationArn": "string",
            "collaborationId": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "id": "string",
            "arn": "string",
            "name": "string",
            "configuredAudienceModelArn": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 9.5 `update-configured-audience-model-association`

Updates an audience model association.

**Synopsis:**
```bash
aws cleanrooms update-configured-audience-model-association \
    --membership-identifier <value> \
    --configured-audience-model-association-identifier <value> \
    [--description <value>] \
    [--name <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--membership-identifier` | **Yes** | string | -- | Membership ID |
| `--configured-audience-model-association-identifier` | **Yes** | string | -- | Association ID |
| `--description` | No | string | None | Updated description |
| `--name` | No | string | None | Updated name |

**Output Schema:**
```json
{
    "configuredAudienceModelAssociation": {
        "id": "string",
        "arn": "string",
        "name": "string",
        "description": "string",
        "updateTime": "timestamp"
    }
}
```

---

## 9.6 `get-collaboration-configured-audience-model-association`

Gets a collaboration-level view of an audience model association.

**Synopsis:**
```bash
aws cleanrooms get-collaboration-configured-audience-model-association \
    --collaboration-identifier <value> \
    --configured-audience-model-association-identifier <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID |
| `--configured-audience-model-association-identifier` | **Yes** | string | -- | Association ID |

**Output Schema:**
```json
{
    "collaborationConfiguredAudienceModelAssociation": {
        "id": "string",
        "arn": "string",
        "collaborationId": "string",
        "collaborationArn": "string",
        "configuredAudienceModelArn": "string",
        "name": "string",
        "description": "string",
        "creatorAccountId": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

## 9.7 `list-collaboration-configured-audience-model-associations`

Lists collaboration audience model associations. **Paginated operation.**

**Synopsis:**
```bash
aws cleanrooms list-collaboration-configured-audience-model-associations \
    --collaboration-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--collaboration-identifier` | **Yes** | string | -- | Collaboration ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "collaborationConfiguredAudienceModelAssociationSummaries": [
        {
            "arn": "string",
            "createTime": "timestamp",
            "id": "string",
            "name": "string",
            "updateTime": "timestamp",
            "collaborationArn": "string",
            "collaborationId": "string",
            "creatorAccountId": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```
