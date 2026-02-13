# AWS HealthLake CLI Reference

AWS HealthLake is a HIPAA-eligible service that enables healthcare organizations to store, transform, query, and analyze health data in the FHIR (Fast Healthcare Interoperability Resources) R4 format at scale.

## Common Workflows

### Create a FHIR Data Store

```bash
# Create a data store with server-side encryption
aws healthlake create-fhir-datastore \
    --datastore-name "my-health-data" \
    --datastore-type-version R4 \
    --sse-configuration KmsEncryptionConfig={CmkType=CUSTOMER_MANAGED_KMS_KEY,KmsKeyId="arn:aws:kms:us-east-1:123456789012:key/my-key"} \
    --preload-data-config PreloadDataType=SYNTHEA

# Wait for data store to become active
aws healthlake wait fhir-datastore-active \
    --datastore-id "abc123def456"

# Verify data store status
aws healthlake describe-fhir-datastore \
    --datastore-id "abc123def456"
```

### Import FHIR Data from S3

```bash
# Start an import job
aws healthlake start-fhir-import-job \
    --datastore-id "abc123def456" \
    --input-data-config S3Uri="s3://my-bucket/fhir-data/" \
    --job-output-data-config S3Configuration={S3Uri="s3://my-bucket/output/",KmsKeyId="arn:aws:kms:us-east-1:123456789012:key/my-key"} \
    --data-access-role-arn "arn:aws:iam::123456789012:role/HealthLakeRole" \
    --job-name "my-import-job"

# Wait for import to complete
aws healthlake wait fhir-import-job-completed \
    --datastore-id "abc123def456" \
    --job-id "import-job-id"

# Check import job status
aws healthlake describe-fhir-import-job \
    --datastore-id "abc123def456" \
    --job-id "import-job-id"
```

### Export FHIR Data to S3

```bash
# Start an export job
aws healthlake start-fhir-export-job \
    --datastore-id "abc123def456" \
    --output-data-config S3Configuration={S3Uri="s3://my-bucket/export/",KmsKeyId="arn:aws:kms:us-east-1:123456789012:key/my-key"} \
    --data-access-role-arn "arn:aws:iam::123456789012:role/HealthLakeRole" \
    --job-name "my-export-job"

# Wait for export to complete
aws healthlake wait fhir-export-job-completed \
    --datastore-id "abc123def456" \
    --job-id "export-job-id"

# List all export jobs for a data store
aws healthlake list-fhir-export-jobs \
    --datastore-id "abc123def456" \
    --job-status COMPLETED
```

### Manage Data Store Lifecycle

```bash
# List all data stores
aws healthlake list-fhir-datastores

# List active data stores only
aws healthlake list-fhir-datastores \
    --filter DatastoreNameFilter="my-health",DatastoreStatusFilter=ACTIVE

# Tag a data store
aws healthlake tag-resource \
    --resource-arn "arn:aws:healthlake:us-east-1:123456789012:datastore/fhir/abc123" \
    --tags '[{"Key":"Environment","Value":"production"}]'

# Delete a data store
aws healthlake delete-fhir-datastore \
    --datastore-id "abc123def456"

# Wait for deletion to complete
aws healthlake wait fhir-datastore-deleted \
    --datastore-id "abc123def456"
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Data Stores | [`datastores.md`](datastores.md) | `create-fhir-datastore`, `describe-fhir-datastore`, `list-fhir-datastores`, `delete-fhir-datastore` |
| Import & Export | [`import-export.md`](import-export.md) | `start-fhir-import-job`, `describe-fhir-import-job`, `list-fhir-import-jobs`, `start-fhir-export-job`, `describe-fhir-export-job`, `list-fhir-export-jobs` |
| Tags | [`tags.md`](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
| Waiters | [`wait.md`](wait.md) | `wait fhir-datastore-active`, `wait fhir-datastore-deleted`, `wait fhir-export-job-completed`, `wait fhir-import-job-completed` |
