# Approval Rules

### 5.1 `create-approval-rule-template`

Creates a template for approval rules that can be associated with repositories.

**Synopsis:**
```bash
aws codecommit create-approval-rule-template \
    --approval-rule-template-name <value> \
    --approval-rule-template-content <value> \
    [--approval-rule-template-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--approval-rule-template-name` | **Yes** | string | -- | Name of the approval rule template (1-100 chars) |
| `--approval-rule-template-content` | **Yes** | string | -- | JSON content defining the approval rule (number of approvals, approval pool members) |
| `--approval-rule-template-description` | No | string | -- | Description of the template |

**Output Schema:**
```json
{
    "approvalRuleTemplate": {
        "approvalRuleTemplateId": "string",
        "approvalRuleTemplateName": "string",
        "approvalRuleTemplateDescription": "string",
        "approvalRuleTemplateContent": "string",
        "ruleContentSha256": "string",
        "lastModifiedDate": "timestamp",
        "creationDate": "timestamp",
        "lastModifiedUser": "string"
    }
}
```

---

### 5.2 `delete-approval-rule-template`

Deletes the specified approval rule template.

**Synopsis:**
```bash
aws codecommit delete-approval-rule-template \
    --approval-rule-template-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--approval-rule-template-name` | **Yes** | string | -- | Name of the approval rule template |

**Output Schema:**
```json
{
    "approvalRuleTemplateId": "string"
}
```

---

### 5.3 `get-approval-rule-template`

Returns information about an approval rule template.

**Synopsis:**
```bash
aws codecommit get-approval-rule-template \
    --approval-rule-template-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--approval-rule-template-name` | **Yes** | string | -- | Name of the approval rule template |

**Output Schema:**
```json
{
    "approvalRuleTemplate": {
        "approvalRuleTemplateId": "string",
        "approvalRuleTemplateName": "string",
        "approvalRuleTemplateDescription": "string",
        "approvalRuleTemplateContent": "string",
        "ruleContentSha256": "string",
        "lastModifiedDate": "timestamp",
        "creationDate": "timestamp",
        "lastModifiedUser": "string"
    }
}
```

---

### 5.4 `list-approval-rule-templates`

Lists all approval rule templates in the account. **Paginated operation.**

**Synopsis:**
```bash
aws codecommit list-approval-rule-templates \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "approvalRuleTemplateNames": ["string"],
    "nextToken": "string"
}
```

---

### 5.5 `update-approval-rule-template-content`

Updates the content of an approval rule template.

**Synopsis:**
```bash
aws codecommit update-approval-rule-template-content \
    --approval-rule-template-name <value> \
    --new-rule-content <value> \
    [--existing-rule-content-sha256 <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--approval-rule-template-name` | **Yes** | string | -- | Name of the approval rule template |
| `--new-rule-content` | **Yes** | string | -- | New JSON content for the approval rule |
| `--existing-rule-content-sha256` | No | string | -- | SHA-256 hash of the existing content (for optimistic locking) |

**Output Schema:**
```json
{
    "approvalRuleTemplate": {
        "approvalRuleTemplateId": "string",
        "approvalRuleTemplateName": "string",
        "approvalRuleTemplateDescription": "string",
        "approvalRuleTemplateContent": "string",
        "ruleContentSha256": "string",
        "lastModifiedDate": "timestamp",
        "creationDate": "timestamp",
        "lastModifiedUser": "string"
    }
}
```

---

### 5.6 `associate-approval-rule-template-with-repository`

Associates an approval rule template with a repository.

**Synopsis:**
```bash
aws codecommit associate-approval-rule-template-with-repository \
    --approval-rule-template-name <value> \
    --repository-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--approval-rule-template-name` | **Yes** | string | -- | Name of the approval rule template |
| `--repository-name` | **Yes** | string | -- | Name of the repository |

**Output Schema:**
```json
{}
```

---

### 5.7 `disassociate-approval-rule-template-from-repository`

Disassociates an approval rule template from a repository.

**Synopsis:**
```bash
aws codecommit disassociate-approval-rule-template-from-repository \
    --approval-rule-template-name <value> \
    --repository-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--approval-rule-template-name` | **Yes** | string | -- | Name of the approval rule template |
| `--repository-name` | **Yes** | string | -- | Name of the repository |

**Output Schema:**
```json
{}
```

---

### 5.8 `list-associated-approval-rule-templates-for-repository`

Lists all approval rule templates associated with a repository. **Paginated operation.**

**Synopsis:**
```bash
aws codecommit list-associated-approval-rule-templates-for-repository \
    --repository-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "approvalRuleTemplateNames": ["string"],
    "nextToken": "string"
}
```

---

### 5.9 `list-repositories-for-approval-rule-template`

Lists all repositories associated with an approval rule template. **Paginated operation.**

**Synopsis:**
```bash
aws codecommit list-repositories-for-approval-rule-template \
    --approval-rule-template-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--approval-rule-template-name` | **Yes** | string | -- | Name of the approval rule template |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "repositoryNames": ["string"],
    "nextToken": "string"
}
```
