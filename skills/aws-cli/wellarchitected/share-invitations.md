# Share Invitations

### 8.1 `list-share-invitations`

Lists share invitations for the account. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-share-invitations \
    [--workload-name-prefix <value>] \
    [--lens-name-prefix <value>] \
    [--share-resource-type <value>] \
    [--profile-name-prefix <value>] \
    [--template-name-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-name-prefix` | No | string | None | Filter by workload name prefix |
| `--lens-name-prefix` | No | string | None | Filter by lens name prefix |
| `--share-resource-type` | No | string | None | `WORKLOAD`, `LENS`, `PROFILE`, or `TEMPLATE` |
| `--profile-name-prefix` | No | string | None | Filter by profile name prefix |
| `--template-name-prefix` | No | string | None | Filter by template name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ShareInvitationSummaries": [
        {
            "ShareInvitationId": "string",
            "SharedBy": "string",
            "SharedWith": "string",
            "PermissionType": "READONLY|CONTRIBUTOR",
            "ShareResourceType": "WORKLOAD|LENS|PROFILE|TEMPLATE",
            "WorkloadName": "string",
            "WorkloadId": "string",
            "LensName": "string",
            "LensArn": "string",
            "ProfileName": "string",
            "ProfileArn": "string",
            "TemplateName": "string",
            "TemplateArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.2 `update-share-invitation`

Accepts or rejects a share invitation.

**Synopsis:**
```bash
aws wellarchitected update-share-invitation \
    --share-invitation-id <value> \
    --share-invitation-action <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--share-invitation-id` | **Yes** | string | -- | Share invitation ID |
| `--share-invitation-action` | **Yes** | string | -- | `ACCEPT` or `REJECT` |

**Output Schema:**
```json
{
    "ShareInvitation": {
        "ShareInvitationId": "string",
        "ShareResourceType": "WORKLOAD|LENS|PROFILE|TEMPLATE",
        "WorkloadId": "string",
        "LensAlias": "string",
        "LensArn": "string",
        "ProfileArn": "string",
        "TemplateArn": "string"
    }
}
```
