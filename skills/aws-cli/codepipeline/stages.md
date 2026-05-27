# Stages

### 2.1 `enable-stage-transition`

Enables artifacts in a pipeline to transition to a stage.

**Synopsis:**
```bash
aws codepipeline enable-stage-transition \
    --pipeline-name <value> \
    --stage-name <value> \
    --transition-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |
| `--stage-name` | **Yes** | string | -- | Stage name |
| `--transition-type` | **Yes** | string | -- | Transition type: `Inbound`, `Outbound` |

**Output Schema:**
```json
{}
```

---

### 2.2 `disable-stage-transition`

Prevents artifacts in a pipeline from transitioning to the next stage.

**Synopsis:**
```bash
aws codepipeline disable-stage-transition \
    --pipeline-name <value> \
    --stage-name <value> \
    --transition-type <value> \
    --reason <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |
| `--stage-name` | **Yes** | string | -- | Stage name |
| `--transition-type` | **Yes** | string | -- | Transition type: `Inbound`, `Outbound` |
| `--reason` | **Yes** | string | -- | Reason for disabling the transition (1-300 chars) |

**Output Schema:**
```json
{}
```

---

### 2.3 `put-approval-result`

Provides the response to a manual approval request in CodePipeline. Valid only on an action with an approval type of `Manual`.

**Synopsis:**
```bash
aws codepipeline put-approval-result \
    --pipeline-name <value> \
    --stage-name <value> \
    --action-name <value> \
    --result <value> \
    --token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |
| `--stage-name` | **Yes** | string | -- | Stage name containing the approval action |
| `--action-name` | **Yes** | string | -- | Approval action name |
| `--result` | **Yes** | structure | -- | Approval result. Shorthand: `summary=string,status=Approved\|Rejected` |
| `--token` | **Yes** | string | -- | System-generated token from the approval action (available in the pipeline state or SNS notification) |

**Output Schema:**
```json
{
    "approvedAt": "timestamp"
}
```
