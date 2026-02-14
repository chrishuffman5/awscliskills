# Experiments

### 3.1 `create-experiment`

Creates an A/B experiment. Experiments compare variations of a feature against a control group using metric goals.

**Synopsis:**
```bash
aws evidently create-experiment \
    --project <value> \
    --name <value> \
    --treatments <value> \
    --metric-goals <value> \
    [--description <value>] \
    [--online-ab-config <value>] \
    [--randomization-salt <value>] \
    [--sampling-rate <value>] \
    [--segment <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN (0-2048 chars) |
| `--name` | **Yes** | string | -- | Experiment name (1-127 chars) |
| `--treatments` | **Yes** | list | -- | Treatment definitions (0-5) |
| `--metric-goals` | **Yes** | list | -- | Metric goal definitions (1-3) |
| `--description` | No | string | None | Description (0-160 chars) |
| `--online-ab-config` | No | structure | None | Control and traffic allocation config |
| `--randomization-salt` | No | string | Experiment name | Salt for randomization (0-127 chars) |
| `--sampling-rate` | No | long | None | Audience portion in thousandths of percent (0-100000) |
| `--segment` | No | string | None | Audience segment to use |
| `--tags` | No | map | None | Tags (max 50) |

**Treatments structure:**
```json
[
    {
        "name": "string",
        "feature": "string",
        "variation": "string",
        "description": "string"
    }
]
```

**MetricGoals structure:**
```json
[
    {
        "desiredChange": "INCREASE|DECREASE",
        "metricDefinition": {
            "name": "string",
            "entityIdKey": "string",
            "valueKey": "string",
            "eventPattern": "string",
            "unitLabel": "string"
        }
    }
]
```

**OnlineAbConfig structure:**
```json
{
    "controlTreatmentName": "string",
    "treatmentWeights": {
        "treatment-name": 50000
    }
}
```

Treatment weights are in thousandths of percent (50000 = 50%).

**Output Schema:**
```json
{
    "experiment": {
        "arn": "string",
        "name": "string",
        "project": "string",
        "description": "string",
        "createdTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "status": "CREATED|UPDATING|RUNNING|COMPLETED|CANCELLED",
        "statusReason": "string",
        "type": "aws.evidently.onlineab",
        "treatments": [],
        "metricGoals": [],
        "onlineAbDefinition": {},
        "randomizationSalt": "string",
        "samplingRate": "long",
        "segment": "string",
        "schedule": {"analysisCompleteTime": "timestamp"},
        "execution": {"startedTime": "timestamp", "endedTime": "timestamp"},
        "tags": {}
    }
}
```

---

### 3.2 `get-experiment`

Retrieves experiment details.

**Synopsis:**
```bash
aws evidently get-experiment \
    --project <value> \
    --experiment <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--experiment` | **Yes** | string | -- | Experiment name (1-127 chars) |

**Output Schema:**
```json
{
    "experiment": {
        "arn": "string",
        "name": "string",
        "project": "string",
        "description": "string",
        "createdTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "status": "CREATED|UPDATING|RUNNING|COMPLETED|CANCELLED",
        "type": "aws.evidently.onlineab",
        "treatments": [],
        "metricGoals": [],
        "onlineAbDefinition": {},
        "execution": {},
        "schedule": {},
        "tags": {}
    }
}
```

---

### 3.3 `list-experiments`

Lists experiments in a project. **Paginated operation.**

**Synopsis:**
```bash
aws evidently list-experiments \
    --project <value> \
    [--status <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--status` | No | string | None | Filter: `CREATED`, `UPDATING`, `RUNNING`, `COMPLETED`, `CANCELLED` |
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |

**Output Schema:**
```json
{
    "nextToken": "string",
    "experiments": [
        {
            "arn": "string",
            "name": "string",
            "project": "string",
            "status": "CREATED|UPDATING|RUNNING|COMPLETED|CANCELLED",
            "type": "aws.evidently.onlineab",
            "createdTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "tags": {}
        }
    ]
}
```

---

### 3.4 `update-experiment`

Updates an experiment. Cannot update a running experiment; stop it first.

**Synopsis:**
```bash
aws evidently update-experiment \
    --project <value> \
    --experiment <value> \
    [--description <value>] \
    [--treatments <value>] \
    [--metric-goals <value>] \
    [--online-ab-config <value>] \
    [--randomization-salt <value>] \
    [--sampling-rate <value>] \
    [--segment <value>] \
    [--remove-segment] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--experiment` | **Yes** | string | -- | Experiment name |
| `--description` | No | string | None | Updated description |
| `--treatments` | No | list | None | Updated treatments |
| `--metric-goals` | No | list | None | Updated metric goals |
| `--online-ab-config` | No | structure | None | Updated A/B config |
| `--randomization-salt` | No | string | None | Updated salt |
| `--sampling-rate` | No | long | None | Updated sampling rate |
| `--segment` | No | string | None | Updated segment |
| `--remove-segment` | No | boolean | None | Remove segment association |

**Output Schema:**
```json
{
    "experiment": {
        "arn": "string",
        "name": "string",
        "project": "string",
        "status": "CREATED|UPDATING|RUNNING|COMPLETED|CANCELLED",
        "treatments": [],
        "metricGoals": [],
        "onlineAbDefinition": {},
        "tags": {}
    }
}
```

---

### 3.5 `delete-experiment`

Deletes an experiment. Must be in CREATED, COMPLETED, or CANCELLED state.

**Synopsis:**
```bash
aws evidently delete-experiment \
    --project <value> \
    --experiment <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--experiment` | **Yes** | string | -- | Experiment name |

**Output:** None

---

### 3.6 `start-experiment`

Starts an experiment.

**Synopsis:**
```bash
aws evidently start-experiment \
    --project <value> \
    --experiment <value> \
    --analysis-complete-time <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--experiment` | **Yes** | string | -- | Experiment name (1-127 chars) |
| `--analysis-complete-time` | **Yes** | timestamp | -- | End time (max 30 days after start) |

**Output Schema:**
```json
{
    "startedTime": "timestamp"
}
```

---

### 3.7 `stop-experiment`

Stops a running experiment.

**Synopsis:**
```bash
aws evidently stop-experiment \
    --project <value> \
    --experiment <value> \
    [--desired-state <value>] \
    [--reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--experiment` | **Yes** | string | -- | Experiment name (1-127 chars) |
| `--desired-state` | No | string | None | `COMPLETED` or `CANCELLED` |
| `--reason` | No | string | None | Reason for stopping (0-160 chars) |

**Output Schema:**
```json
{
    "endedTime": "timestamp"
}
```

---

### 3.8 `get-experiment-results`

Retrieves experiment results and statistical analysis.

**Synopsis:**
```bash
aws evidently get-experiment-results \
    --project <value> \
    --experiment <value> \
    --metric-names <value> \
    --treatment-names <value> \
    [--base-stat <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--period <value>] \
    [--report-names <value>] \
    [--result-stats <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--experiment` | **Yes** | string | -- | Experiment name (1-127 chars) |
| `--metric-names` | **Yes** | list | -- | Metric names (1 metric) |
| `--treatment-names` | **Yes** | list | -- | Treatment names (1-5) |
| `--base-stat` | No | string | None | `Mean` |
| `--start-time` | No | timestamp | None | Results start time |
| `--end-time` | No | timestamp | None | Results end time (max 30 days after start) |
| `--period` | No | long | None | Aggregation period in seconds (300-90000) |
| `--report-names` | No | list | None | `BayesianInference` (0-5) |
| `--result-stats` | No | list | None | `BaseStat`, `TreatmentEffect`, `ConfidenceInterval`, `PValue` (0-5) |

Results require at least 100 events per variation and 10 minutes since experiment start. Results available up to 63 days after experiment start.

**Output Schema:**
```json
{
    "details": "string",
    "reports": [
        {
            "content": "string",
            "metricName": "string",
            "reportName": "BayesianInference",
            "treatmentName": "string"
        }
    ],
    "resultsData": [
        {
            "metricName": "string",
            "resultStat": "Mean|TreatmentEffect|ConfidenceIntervalUpperBound|ConfidenceIntervalLowerBound|PValue",
            "treatmentName": "string",
            "values": ["double"]
        }
    ],
    "timestamps": ["timestamp"]
}
```
