# Topics

Amazon QuickSight Q topics enable natural language querying of data. Topics define the data and business semantics that Q uses to answer questions.

### 13.1 `create-topic`

Creates a Q topic.

**Synopsis:**
```bash
aws quicksight create-topic \
    --aws-account-id <value> \
    --topic-id <value> \
    --topic <value> \
    [--tags <value>] \
    [--folder-arns <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--topic-id` | **Yes** | string | -- | Topic ID |
| `--topic` | **Yes** | structure | -- | Topic definition (name, description, data sets, columns, metrics) |
| `--tags` | No | list | None | Resource tags |
| `--folder-arns` | No | list(string) | None | Folder ARNs |

**Output Schema:**
```json
{
    "Arn": "string",
    "TopicId": "string",
    "RefreshArn": "string",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 13.2 `describe-topic` / `update-topic` / `delete-topic`

Manage topics.

**Synopsis:**
```bash
aws quicksight describe-topic --aws-account-id <value> --topic-id <value>
aws quicksight update-topic --aws-account-id <value> --topic-id <value> --topic <value>
aws quicksight delete-topic --aws-account-id <value> --topic-id <value>
```

---

### 13.3 `list-topics` / `search-topics`

List or search topics. **Paginated operations.**

**Synopsis:**
```bash
aws quicksight list-topics --aws-account-id <value>
aws quicksight search-topics --aws-account-id <value> --filters <value>
```

---

### 13.4 `describe-topic-permissions` / `update-topic-permissions`

Manage topic permissions.

**Synopsis:**
```bash
aws quicksight describe-topic-permissions --aws-account-id <value> --topic-id <value>
aws quicksight update-topic-permissions --aws-account-id <value> --topic-id <value> \
    [--grant-permissions <value>] [--revoke-permissions <value>]
```

---

### 13.5 `describe-topic-refresh` / `describe-topic-refresh-schedule` / `update-topic-refresh-schedule` / `list-topic-refresh-schedules`

Manage topic refresh.

**Synopsis:**
```bash
aws quicksight describe-topic-refresh \
    --aws-account-id <value> --topic-id <value> --refresh-id <value>

aws quicksight describe-topic-refresh-schedule \
    --aws-account-id <value> --topic-id <value> --dataset-id <value>

aws quicksight update-topic-refresh-schedule \
    --aws-account-id <value> --topic-id <value> --dataset-id <value> \
    --refresh-schedule <value>

aws quicksight list-topic-refresh-schedules \
    --aws-account-id <value> --topic-id <value>
```

---

### 13.6 `batch-create-topic-reviewed-answer` / `batch-delete-topic-reviewed-answer` / `list-topic-reviewed-answers`

Manage reviewed Q&A answers for a topic.

**Synopsis:**
```bash
aws quicksight batch-create-topic-reviewed-answer \
    --aws-account-id <value> --topic-id <value> --answers <value>

aws quicksight batch-delete-topic-reviewed-answer \
    --aws-account-id <value> --topic-id <value> --answer-ids <value>

aws quicksight list-topic-reviewed-answers \
    --aws-account-id <value> --topic-id <value>
```
