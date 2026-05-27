# HealthLake Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-fhir-datastore` | Creates a FHIR R4 data store |
| `delete-fhir-datastore` | Deletes a FHIR data store |
| `describe-fhir-datastore` | Gets properties of a data store |
| `describe-fhir-export-job` | Gets properties of a FHIR export job |
| `describe-fhir-import-job` | Gets properties of a FHIR import job |
| `list-fhir-datastores` | Lists FHIR data stores with optional filters |
| `list-fhir-export-jobs` | Lists FHIR export jobs for a data store |
| `list-fhir-import-jobs` | Lists FHIR import jobs for a data store |
| `list-tags-for-resource` | Lists tags for a data store |
| `start-fhir-export-job` | Starts a FHIR data export job to S3 |
| `start-fhir-import-job` | Starts a FHIR data import job from S3 |
| `tag-resource` | Adds tags to a data store |
| `untag-resource` | Removes tags from a data store |
| `wait fhir-datastore-active` | Waits until data store is ACTIVE |
| `wait fhir-datastore-deleted` | Waits until data store is DELETED |
| `wait fhir-export-job-completed` | Waits until export job is COMPLETED |
| `wait fhir-import-job-completed` | Waits until import job is COMPLETED |

## Data Store Statuses

| Status | Description |
|--------|-------------|
| `CREATING` | Data store is being provisioned |
| `ACTIVE` | Data store is ready for use |
| `DELETING` | Data store is being deleted |
| `DELETED` | Data store has been deleted |
| `CREATE_FAILED` | Data store creation failed |

## Job Statuses

| Status | Description |
|--------|-------------|
| `SUBMITTED` | Job has been submitted |
| `QUEUED` | Job is queued for processing |
| `IN_PROGRESS` | Job is currently running |
| `COMPLETED` | Job finished successfully |
| `COMPLETED_WITH_ERRORS` | Job finished with some errors |
| `FAILED` | Job failed |
| `CANCEL_SUBMITTED` | Cancellation requested |
| `CANCEL_IN_PROGRESS` | Cancellation in progress |
| `CANCEL_COMPLETED` | Cancellation completed |
| `CANCEL_FAILED` | Cancellation failed |

## Key Concepts

- **FHIR R4**: Only version supported. Fast Healthcare Interoperability Resources Release 4.
- **Preload Data**: Optional SYNTHEA sample data loaded at creation.
- **SSE Configuration**: Server-side encryption using AWS-owned or customer-managed KMS keys.
- **SMART on FHIR**: Optional authorization with OpenID Connect identity provider.
- **Identity Resolution**: Optional identity resolution using LAMBDA strategy.

## Global Options

All `aws healthlake` commands support these options:

| Option | Description |
|--------|-------------|
| `--region` | AWS region |
| `--profile` | Named profile |
| `--output` | Output format: `json`, `text`, `table`, `yaml` |
| `--query` | JMESPath query |
| `--no-cli-pager` | Disable pager |
| `--cli-input-json` | Read input from JSON |
| `--generate-cli-skeleton` | Generate input skeleton |
