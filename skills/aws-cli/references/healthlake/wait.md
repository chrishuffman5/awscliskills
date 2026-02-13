# Waiters

All waiters poll an underlying API at fixed intervals until a target state is reached or max attempts are exceeded (exit code 255).

### 4.1 `wait fhir-datastore-active`

Waits until a data store reaches ACTIVE status.

**Synopsis:**
```bash
aws healthlake wait fhir-datastore-active \
    --datastore-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-id` | **Yes** | string | -- | Data store ID (1-32 chars) |

**Behavior:**
- Polls `describe-fhir-datastore` every **60 seconds**
- Succeeds when `DatastoreProperties.DatastoreStatus` returns `ACTIVE`
- Max **360** attempts before timeout

---

### 4.2 `wait fhir-datastore-deleted`

Waits until a data store reaches DELETED status.

**Synopsis:**
```bash
aws healthlake wait fhir-datastore-deleted \
    --datastore-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-id` | **Yes** | string | -- | Data store ID (1-32 chars) |

**Behavior:**
- Polls `describe-fhir-datastore` every **120 seconds**
- Succeeds when `DatastoreProperties.DatastoreStatus` returns `DELETED`
- Max **360** attempts before timeout

---

### 4.3 `wait fhir-export-job-completed`

Waits until a FHIR export job completes.

**Synopsis:**
```bash
aws healthlake wait fhir-export-job-completed \
    --datastore-id <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-id` | **Yes** | string | -- | Data store ID (1-32 chars) |
| `--job-id` | **Yes** | string | -- | Export job ID (1-32 chars) |

**Behavior:**
- Polls `describe-fhir-export-job` every **120 seconds**
- Succeeds when `ExportJobProperties.JobStatus` returns `COMPLETED`
- Max **360** attempts before timeout

---

### 4.4 `wait fhir-import-job-completed`

Waits until a FHIR import job completes.

**Synopsis:**
```bash
aws healthlake wait fhir-import-job-completed \
    --datastore-id <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-id` | **Yes** | string | -- | Data store ID (1-32 chars) |
| `--job-id` | **Yes** | string | -- | Import job ID (1-32 chars) |

**Behavior:**
- Polls `describe-fhir-import-job` every **120 seconds**
- Succeeds when `ImportJobProperties.JobStatus` returns `COMPLETED`
- Max **720** attempts before timeout
