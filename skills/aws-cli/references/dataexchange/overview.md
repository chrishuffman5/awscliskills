# AWS CLI v2 — Data Exchange

## Overview

Complete reference for `aws dataexchange` subcommands in AWS CLI v2. Covers data set management, revision and asset lifecycle, import/export jobs, data grants, event actions, and resource tagging. AWS Data Exchange enables secure exchange of data sets between data providers and subscribers.

## Quick Reference — Common Workflows

### Create a data set
```bash
aws dataexchange create-data-set \
  --asset-type S3_SNAPSHOT \
  --name "My Dataset" \
  --description "Sales data for Q4 2025"
```

### Create a revision and import assets from S3
```bash
aws dataexchange create-revision \
  --data-set-id abc123def456 \
  --comment "January 2026 data"

aws dataexchange create-job \
  --type IMPORT_ASSETS_FROM_S3 \
  --details '{"ImportAssetsFromS3":{"DataSetId":"abc123def456","RevisionId":"rev789","AssetSources":[{"Bucket":"my-bucket","Key":"data/file.csv"}]}}'

aws dataexchange start-job --job-id job-xyz
```

### Export assets to S3
```bash
aws dataexchange create-job \
  --type EXPORT_ASSETS_TO_S3 \
  --details '{"ExportAssetsToS3":{"DataSetId":"abc123def456","RevisionId":"rev789","AssetDestinations":[{"AssetId":"asset-123","Bucket":"export-bucket","Key":"exports/file.csv"}]}}'

aws dataexchange start-job --job-id job-xyz
```

### Create a data grant for cross-account sharing
```bash
aws dataexchange create-data-grant \
  --name "Partner Data Grant" \
  --grant-distribution-scope NONE \
  --receiver-principal 987654321098 \
  --source-data-set-id abc123def456
```

### Set up auto-export on new revisions
```bash
aws dataexchange create-event-action \
  --event '{"RevisionPublished":{"DataSetId":"abc123def456"}}' \
  --action '{"ExportRevisionToS3":{"RevisionDestination":{"Bucket":"export-bucket","KeyPattern":"${Revision.CreatedAt}/${Asset.Name}"},"Encryption":{"Type":"AES256"}}}'
```

### List and finalize a revision
```bash
aws dataexchange list-data-set-revisions --data-set-id abc123def456
aws dataexchange update-revision --data-set-id abc123def456 --revision-id rev789 --finalized
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Data Sets | [`data-sets.md`](data-sets.md) | create-data-set, get-data-set, list-data-sets, update-data-set, delete-data-set, send-data-set-notification |
| Revisions & Assets | [`revisions-assets.md`](revisions-assets.md) | create-revision, get-revision, list-data-set-revisions, update-revision, delete-revision, revoke-revision, get-asset, list-revision-assets, update-asset, delete-asset, send-api-asset |
| Jobs | [`jobs.md`](jobs.md) | create-job, start-job, get-job, list-jobs, cancel-job |
| Data Grants | [`data-grants.md`](data-grants.md) | create-data-grant, get-data-grant, list-data-grants, delete-data-grant, accept-data-grant, get-received-data-grant, list-received-data-grants |
| Event Actions & Tags | [`event-actions-tags.md`](event-actions-tags.md) | create-event-action, get-event-action, list-event-actions, update-event-action, delete-event-action, tag-resource, untag-resource, list-tags-for-resource |
