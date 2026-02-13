# AWS CLI v2 — Clean Rooms (AWS Clean Rooms + Clean Rooms ML)

## Overview

Complete reference for `aws cleanrooms` and `aws cleanroomsml` subcommands in AWS CLI v2. AWS Clean Rooms enables organizations to collaborate on data without sharing raw data. Covers collaboration management, memberships, configured tables, analysis templates, schemas, protected queries, privacy budgets, ID mapping, and Clean Rooms ML for audience modeling, training, inference, and audience generation.

## Quick Reference — Common Workflows

### Create a collaboration
```bash
aws cleanrooms create-collaboration \
  --name "Marketing Collaboration" \
  --members file://members.json \
  --creator-member-abilities '["CAN_QUERY","CAN_RECEIVE_RESULTS"]' \
  --creator-display-name "Advertiser" \
  --query-log-status ENABLED \
  --description "Cross-org marketing analysis"
```

### Create a configured table and analysis rule
```bash
aws cleanrooms create-configured-table \
  --name "Sales Table" \
  --table-reference '{"Glue":{"TableName":"sales","DatabaseName":"analytics"}}' \
  --allowed-columns '["customer_id","purchase_amount","category"]' \
  --analysis-method DIRECT_QUERY

aws cleanrooms create-configured-table-analysis-rule \
  --configured-table-identifier ct-abc123 \
  --analysis-rule-type AGGREGATION \
  --analysis-rule-policy file://aggregation-policy.json
```

### Join a collaboration as a member
```bash
aws cleanrooms create-membership \
  --collaboration-identifier collab-abc123 \
  --query-log-status ENABLED
```

### Run a protected query
```bash
aws cleanrooms start-protected-query \
  --type SQL \
  --membership-identifier mem-abc123 \
  --sql-parameters '{"QueryString":"SELECT category, COUNT(*) FROM sales GROUP BY category"}' \
  --result-configuration '{"OutputConfiguration":{"S3":{"ResultFormat":"CSV","Bucket":"results-bucket","KeyPrefix":"output/"}}}'
```

### Create an audience model (Clean Rooms ML)
```bash
aws cleanroomsml create-audience-model \
  --name "Lookalike Model" \
  --training-data-arn arn:aws:cleanrooms-ml:us-east-1:123456789012:training-dataset/td-abc

aws cleanroomsml create-configured-audience-model \
  --name "Configured Lookalike" \
  --audience-model-arn arn:aws:cleanrooms-ml:us-east-1:123456789012:audience-model/am-abc \
  --output-config '{"Destination":{"S3Destination":{"S3Uri":"s3://output-bucket/audiences/"}}}'
```

### Start an audience generation job
```bash
aws cleanroomsml start-audience-generation-job \
  --name "Q1 Lookalike" \
  --configured-audience-model-arn arn:aws:cleanrooms-ml:... \
  --seed-audience '{"DataSource":{"S3Uri":"s3://seed-bucket/seed.csv"},"RoleArn":"arn:aws:iam::123456789012:role/SeedRole"}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Collaborations | [`collaborations.md`](collaborations.md) | create-collaboration, delete-collaboration, get-collaboration, list-collaborations, update-collaboration, create-collaboration-change-request, get-collaboration-change-request, list-collaboration-change-requests, update-collaboration-change-request |
| Memberships | [`memberships.md`](memberships.md) | create-membership, delete-membership, get-membership, list-memberships, update-membership, delete-member, list-members |
| Configured Tables | [`configured-tables.md`](configured-tables.md) | create-configured-table, delete-configured-table, get-configured-table, list-configured-tables, update-configured-table, create-configured-table-analysis-rule, delete-configured-table-analysis-rule, get-configured-table-analysis-rule, update-configured-table-analysis-rule, create-configured-table-association, delete-configured-table-association, get-configured-table-association, list-configured-table-associations, update-configured-table-association, create-configured-table-association-analysis-rule, delete-configured-table-association-analysis-rule, get-configured-table-association-analysis-rule, update-configured-table-association-analysis-rule |
| Analysis Templates | [`analysis-templates.md`](analysis-templates.md) | create-analysis-template, delete-analysis-template, get-analysis-template, list-analysis-templates, update-analysis-template, batch-get-collaboration-analysis-template, get-collaboration-analysis-template, list-collaboration-analysis-templates |
| Schemas | [`schemas.md`](schemas.md) | batch-get-schema, batch-get-schema-analysis-rule, get-schema, get-schema-analysis-rule, list-schemas |
| Protected Queries | [`protected-queries.md`](protected-queries.md) | start-protected-query, get-protected-query, list-protected-queries, update-protected-query, start-protected-job, get-protected-job, list-protected-jobs, update-protected-job |
| Privacy Budgets | [`privacy-budgets.md`](privacy-budgets.md) | create-privacy-budget-template, delete-privacy-budget-template, get-privacy-budget-template, list-privacy-budget-templates, list-privacy-budgets, update-privacy-budget-template, get-collaboration-privacy-budget-template, list-collaboration-privacy-budget-templates, list-collaboration-privacy-budgets, preview-privacy-impact, tag-resource, untag-resource, list-tags-for-resource |
| ID Mapping | [`id-mapping.md`](id-mapping.md) | create-id-mapping-table, delete-id-mapping-table, get-id-mapping-table, list-id-mapping-tables, populate-id-mapping-table, update-id-mapping-table, create-id-namespace-association, delete-id-namespace-association, get-id-namespace-association, list-id-namespace-associations, update-id-namespace-association, get-collaboration-id-namespace-association, list-collaboration-id-namespace-associations |
| Audience Model Associations | [`audience-model-assoc.md`](audience-model-assoc.md) | create-configured-audience-model-association, delete-configured-audience-model-association, get-configured-audience-model-association, list-configured-audience-model-associations, update-configured-audience-model-association, get-collaboration-configured-audience-model-association, list-collaboration-configured-audience-model-associations |
| ML Audience Models | [`ml-audience-models.md`](ml-audience-models.md) | create-audience-model, delete-audience-model, get-audience-model, list-audience-models, create-configured-audience-model, delete-configured-audience-model, get-configured-audience-model, list-configured-audience-models, update-configured-audience-model |
| ML Training | [`ml-training.md`](ml-training.md) | create-training-dataset, delete-training-dataset, get-training-dataset, list-training-datasets, create-ml-input-channel, delete-ml-input-channel-data, get-ml-input-channel, list-ml-input-channels, get-collaboration-ml-input-channel, list-collaboration-ml-input-channels |
| ML Trained Models | [`ml-trained-models.md`](ml-trained-models.md) | create-trained-model, cancel-trained-model, delete-trained-model-output, get-trained-model, list-trained-models, list-trained-model-versions, get-collaboration-trained-model, list-collaboration-trained-models |
| ML Inference | [`ml-inference.md`](ml-inference.md) | start-trained-model-inference-job, cancel-trained-model-inference-job, get-trained-model-inference-job, list-trained-model-inference-jobs, start-trained-model-export-job, list-collaboration-trained-model-export-jobs, list-collaboration-trained-model-inference-jobs |
| ML Algorithms | [`ml-algorithms.md`](ml-algorithms.md) | create-configured-model-algorithm, delete-configured-model-algorithm, get-configured-model-algorithm, list-configured-model-algorithms, create-configured-model-algorithm-association, delete-configured-model-algorithm-association, get-configured-model-algorithm-association, list-configured-model-algorithm-associations, get-collaboration-configured-model-algorithm-association, list-collaboration-configured-model-algorithm-associations |
| ML Audience Generation | [`ml-audience-generation.md`](ml-audience-generation.md) | start-audience-generation-job, delete-audience-generation-job, get-audience-generation-job, list-audience-generation-jobs, start-audience-export-job, list-audience-export-jobs, delete-configured-audience-model-policy, get-configured-audience-model-policy, put-configured-audience-model-policy, delete-ml-configuration, get-ml-configuration, put-ml-configuration, tag-resource, untag-resource, list-tags-for-resource |
