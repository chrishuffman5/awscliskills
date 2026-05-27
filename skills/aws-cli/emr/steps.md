# Steps

### 3.1 `add-steps`

Adds steps to a running cluster.

**Synopsis:**
```bash
aws emr add-steps \
    --cluster-id <value> \
    --steps <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster to add steps to |
| `--steps` | **Yes** | list | -- | Step definitions (see formats below) |

**Step Shorthand Formats:**

Spark step:
```
Type=Spark,Name="My Spark Job",ActionOnFailure=CONTINUE,\
Args=[--class,com.example.Main,s3://bucket/app.jar,arg1]
```

Custom JAR step:
```
Type=CUSTOM_JAR,Name="Custom Step",Jar=s3://bucket/step.jar,\
ActionOnFailure=CANCEL_AND_WAIT,Args=[arg1,arg2]
```

Hive step:
```
Type=Hive,Name="Hive Job",ActionOnFailure=CONTINUE,\
Args=[-f,s3://bucket/script.hql,-d,INPUT=s3://input,-d,OUTPUT=s3://output]
```

Streaming step:
```
Type=STREAMING,Name="Streaming Job",ActionOnFailure=CONTINUE,\
Args=[-files,s3://bucket/mapper.py,-mapper,mapper.py,-reducer,aggregate,\
-input,s3://input,-output,s3://output]
```

**ActionOnFailure Values:**
- `TERMINATE_CLUSTER` — Terminate the cluster
- `CANCEL_AND_WAIT` — Cancel remaining steps, keep cluster running
- `CONTINUE` — Continue to next step

**Output Schema:**
```json
{
    "StepIds": ["string"]
}
```

---

### 3.2 `cancel-steps`

Cancels pending steps in a running cluster.

**Synopsis:**
```bash
aws emr cancel-steps \
    --cluster-id <value> \
    --step-ids <value> \
    [--step-cancellation-option <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--step-ids` | **Yes** | list(string) | -- | Step IDs to cancel |
| `--step-cancellation-option` | No | string | `SEND_INTERRUPT` | `SEND_INTERRUPT` or `TERMINATE_PROCESS` |

**Output Schema:**
```json
{
    "CancelStepsInfoList": [
        {
            "StepId": "string",
            "Status": "SUBMITTED|FAILED",
            "Reason": "string"
        }
    ]
}
```

---

### 3.3 `list-steps`

Lists the steps in a cluster, optionally filtered by state. **Paginated operation.**

**Synopsis:**
```bash
aws emr list-steps \
    --cluster-id <value> \
    [--step-states <value>] \
    [--step-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--step-states` | No | list(string) | -- | Filter: `PENDING`, `CANCEL_PENDING`, `RUNNING`, `COMPLETED`, `CANCELLED`, `FAILED`, `INTERRUPTED` |
| `--step-ids` | No | list(string) | -- | Specific step IDs |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Steps": [
        {
            "Id": "string",
            "Name": "string",
            "Config": {
                "Jar": "string",
                "Properties": {},
                "MainClass": "string",
                "Args": ["string"]
            },
            "ActionOnFailure": "TERMINATE_CLUSTER|CANCEL_AND_WAIT|CONTINUE",
            "Status": {
                "State": "PENDING|CANCEL_PENDING|RUNNING|COMPLETED|CANCELLED|FAILED|INTERRUPTED",
                "StateChangeReason": {
                    "Code": "string",
                    "Message": "string"
                },
                "FailureDetails": {
                    "Reason": "string",
                    "Message": "string",
                    "LogFile": "string"
                },
                "Timeline": {
                    "CreationDateTime": "timestamp",
                    "StartDateTime": "timestamp",
                    "EndDateTime": "timestamp"
                }
            }
        }
    ],
    "Marker": "string"
}
```

---

### 3.4 `describe-step`

Describes a specific step.

**Synopsis:**
```bash
aws emr describe-step \
    --cluster-id <value> \
    --step-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--step-id` | **Yes** | string | -- | Step ID |

**Output Schema:**
```json
{
    "Step": {
        "Id": "string",
        "Name": "string",
        "Config": {
            "Jar": "string",
            "Properties": {},
            "MainClass": "string",
            "Args": ["string"]
        },
        "ActionOnFailure": "string",
        "Status": {
            "State": "string",
            "StateChangeReason": {},
            "FailureDetails": {},
            "Timeline": {}
        }
    }
}
```
