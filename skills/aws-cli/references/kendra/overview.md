# AWS CLI v2 — Kendra (Intelligent Search + Intelligent Ranking)

## Overview

Complete reference for `aws kendra` and `aws kendra-ranking` subcommands in AWS CLI v2. Amazon Kendra is an intelligent search service that uses natural language processing and machine learning to return relevant answers from your data. It supports multiple data source connectors, FAQs, thesauri, query suggestions, featured results, access control, and search experiences. Amazon Kendra Intelligent Ranking provides semantic re-ranking of search results from external search services.

## Quick Reference — Common Workflows

### Create an index
```bash
aws kendra create-index \
  --name my-index \
  --role-arn arn:aws:iam::123456789012:role/KendraRole \
  --edition DEVELOPER_EDITION
```

### Create an S3 data source and sync
```bash
aws kendra create-data-source \
  --index-id <index-id> \
  --name my-s3-source \
  --type S3 \
  --role-arn arn:aws:iam::123456789012:role/KendraS3Role \
  --configuration '{"S3Configuration":{"BucketName":"my-bucket"}}'

aws kendra start-data-source-sync-job \
  --index-id <index-id> \
  --id <data-source-id>
```

### Query the index
```bash
aws kendra query \
  --index-id <index-id> \
  --query-text "How do I reset my password?"
```

### Retrieve passages for RAG/LLM
```bash
aws kendra retrieve \
  --index-id <index-id> \
  --query-text "How do I reset my password?" \
  --page-size 10
```

### Add an FAQ
```bash
aws kendra create-faq \
  --index-id <index-id> \
  --name my-faq \
  --s3-path '{"Bucket":"my-bucket","Key":"faq.csv"}' \
  --role-arn arn:aws:iam::123456789012:role/KendraFaqRole \
  --file-format CSV_WITH_HEADER
```

### Create a thesaurus for synonym matching
```bash
aws kendra create-thesaurus \
  --index-id <index-id> \
  --name my-thesaurus \
  --source-s3-path '{"Bucket":"my-bucket","Key":"thesaurus.txt"}' \
  --role-arn arn:aws:iam::123456789012:role/KendraRole
```

### Re-rank search results with Kendra Intelligent Ranking
```bash
aws kendra-ranking create-rescore-execution-plan \
  --name my-rescore-plan

aws kendra-ranking rescore \
  --rescore-execution-plan-id <plan-id> \
  --search-query "reset password" \
  --documents '[{"Id":"doc1","OriginalScore":5.0,"Title":"Password Reset","Body":"Steps to reset your password..."}]'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Indexes | [`indexes.md`](indexes.md) | create-index, delete-index, describe-index, list-indices, update-index |
| Data Sources | [`data-sources.md`](data-sources.md) | create-data-source, delete-data-source, describe-data-source, list-data-sources, update-data-source, start-data-source-sync-job, stop-data-source-sync-job, list-data-source-sync-jobs, batch-delete-document, batch-get-document-status, batch-put-document, query, retrieve, get-snapshots, submit-feedback |
| FAQs | [`faqs.md`](faqs.md) | create-faq, delete-faq, describe-faq, list-faqs |
| Thesauri | [`thesauri.md`](thesauri.md) | create-thesaurus, delete-thesaurus, describe-thesaurus, list-thesauri, update-thesaurus |
| Query Suggestions | [`query-suggestions.md`](query-suggestions.md) | get-query-suggestions, describe-query-suggestions-config, update-query-suggestions-config, clear-query-suggestions, create-query-suggestions-block-list, delete-query-suggestions-block-list, describe-query-suggestions-block-list, list-query-suggestions-block-lists, update-query-suggestions-block-list |
| Featured Results | [`featured-results.md`](featured-results.md) | create-featured-results-set, delete-featured-results-set, describe-featured-results-set, list-featured-results-sets, update-featured-results-set |
| Access Control | [`access-control.md`](access-control.md) | create-access-control-configuration, delete-access-control-configuration, describe-access-control-configuration, list-access-control-configurations, update-access-control-configuration, put-principal-mapping, delete-principal-mapping, describe-principal-mapping, list-groups-older-than-ordering-id |
| Experiences | [`experiences.md`](experiences.md) | create-experience, delete-experience, describe-experience, list-experiences, update-experience, associate-entities-to-experience, disassociate-entities-from-experience, list-experience-entities, associate-personas-to-entities, disassociate-personas-from-entities, list-entity-personas |
| Ranking | [`ranking.md`](ranking.md) | create-rescore-execution-plan, delete-rescore-execution-plan, describe-rescore-execution-plan, list-rescore-execution-plans, update-rescore-execution-plan, rescore |
| Rules & Tags | [`rules-tags.md`](rules-tags.md) | tag-resource, untag-resource, list-tags-for-resource |
