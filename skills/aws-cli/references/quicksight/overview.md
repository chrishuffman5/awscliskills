# AWS CLI v2 — QuickSight

## Overview

Complete reference for all `aws quicksight` subcommands in AWS CLI v2. Covers account management, dashboards, analyses, templates, themes, data sets, data sources, ingestions, folders, users and groups, namespaces, IAM policy assignments, topics (Q), VPC connections, embedding, asset bundle import/export, brands, action connectors, custom permissions, identity/key management, and flows. Amazon QuickSight is a cloud-native BI service for creating interactive dashboards, reports, and embedded analytics.

## Quick Reference — Common Workflows

### Register a new user
```bash
aws quicksight register-user --aws-account-id 123456789012 \
  --namespace default --identity-type IAM \
  --iam-arn arn:aws:iam::123456789012:user/analyst \
  --email analyst@example.com --user-role READER
```

### Create a data source
```bash
aws quicksight create-data-source --aws-account-id 123456789012 \
  --data-source-id my-rds-source --name "My RDS Source" \
  --type AURORA_POSTGRESQL \
  --data-source-parameters '{"AuroraPostgreSqlParameters":{"Host":"mydb.cluster-xxx.us-east-1.rds.amazonaws.com","Port":5432,"Database":"analytics"}}' \
  --credentials '{"CredentialPair":{"Username":"admin","Password":"secret"}}'
```

### Create a data set
```bash
aws quicksight create-data-set --aws-account-id 123456789012 \
  --data-set-id my-dataset --name "Sales Data" \
  --import-mode SPICE \
  --physical-table-map '{"sales":{"RelationalTable":{"DataSourceArn":"arn:aws:quicksight:...","Schema":"public","Name":"sales","InputColumns":[{"Name":"id","Type":"INTEGER"},{"Name":"amount","Type":"DECIMAL"}]}}}'
```

### Create a dashboard from a template
```bash
aws quicksight create-dashboard --aws-account-id 123456789012 \
  --dashboard-id my-dashboard --name "Sales Dashboard" \
  --source-entity '{"SourceTemplate":{"DataSetReferences":[{"DataSetPlaceholder":"sales","DataSetArn":"arn:aws:quicksight:..."}],"Arn":"arn:aws:quicksight:...:template/my-template"}}'
```

### List dashboards
```bash
aws quicksight list-dashboards --aws-account-id 123456789012
```

### Generate embed URL for registered user
```bash
aws quicksight generate-embed-url-for-registered-user \
  --aws-account-id 123456789012 \
  --user-arn "arn:aws:quicksight:us-east-1:123456789012:user/default/analyst" \
  --experience-configuration '{"Dashboard":{"InitialDashboardId":"my-dashboard"}}'
```

### Start an asset bundle export
```bash
aws quicksight start-asset-bundle-export-job \
  --aws-account-id 123456789012 \
  --asset-bundle-export-job-id my-export \
  --resource-arns "arn:aws:quicksight:us-east-1:123456789012:dashboard/my-dashboard" \
  --include-all-dependencies \
  --export-format QUICKSIGHT_JSON
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Account | [`account.md`](account.md) | create-account-customization, describe-account-customization, update-account-customization, delete-account-customization, describe-account-settings, update-account-settings, describe-account-subscription, create-account-subscription, delete-account-subscription |
| Dashboards | [`dashboards.md`](dashboards.md) | create-dashboard, describe-dashboard, describe-dashboard-definition, update-dashboard, delete-dashboard, list-dashboards, list-dashboard-versions, search-dashboards, update-dashboard-published-version, update-dashboard-links, describe-dashboard-permissions, update-dashboard-permissions, describe-dashboards-qa-configuration, update-dashboards-qa-configuration |
| Dashboard Snapshots | [`dashboard-snapshots.md`](dashboard-snapshots.md) | start-dashboard-snapshot-job, describe-dashboard-snapshot-job, describe-dashboard-snapshot-job-result, start-dashboard-snapshot-job-schedule |
| Analyses | [`analyses.md`](analyses.md) | create-analysis, describe-analysis, describe-analysis-definition, update-analysis, delete-analysis, list-analyses, search-analyses, restore-analysis, describe-analysis-permissions, update-analysis-permissions |
| Templates | [`templates.md`](templates.md) | create-template, describe-template, describe-template-definition, update-template, delete-template, list-templates, list-template-versions, describe-template-permissions, update-template-permissions, create-template-alias, describe-template-alias, update-template-alias, delete-template-alias, list-template-aliases |
| Themes | [`themes.md`](themes.md) | create-theme, describe-theme, update-theme, delete-theme, list-themes, list-theme-versions, describe-theme-permissions, update-theme-permissions, create-theme-alias, describe-theme-alias, update-theme-alias, delete-theme-alias, list-theme-aliases |
| Data Sets | [`data-sets.md`](data-sets.md) | create-data-set, describe-data-set, update-data-set, delete-data-set, list-data-sets, search-data-sets, describe-data-set-permissions, update-data-set-permissions, describe-data-set-refresh-properties, put-data-set-refresh-properties, delete-data-set-refresh-properties |
| Data Sources | [`data-sources.md`](data-sources.md) | create-data-source, describe-data-source, update-data-source, delete-data-source, list-data-sources, search-data-sources, describe-data-source-permissions, update-data-source-permissions |
| Ingestions | [`ingestions.md`](ingestions.md) | create-ingestion, describe-ingestion, list-ingestions, cancel-ingestion, create-refresh-schedule, describe-refresh-schedule, update-refresh-schedule, delete-refresh-schedule, list-refresh-schedules |
| Folders | [`folders.md`](folders.md) | create-folder, describe-folder, update-folder, delete-folder, list-folders, search-folders, create-folder-membership, delete-folder-membership, list-folder-members, list-folders-for-resource, describe-folder-permissions, describe-folder-resolved-permissions, update-folder-permissions |
| Users & Groups | [`users-groups.md`](users-groups.md) | register-user, describe-user, update-user, delete-user, delete-user-by-principal-id, list-users, create-group, describe-group, update-group, delete-group, list-groups, search-groups, create-group-membership, describe-group-membership, delete-group-membership, list-group-memberships, list-user-groups |
| Namespaces & IAM | [`namespaces-iam.md`](namespaces-iam.md) | create-namespace, describe-namespace, delete-namespace, list-namespaces, create-iam-policy-assignment, describe-iam-policy-assignment, update-iam-policy-assignment, delete-iam-policy-assignment, list-iam-policy-assignments, list-iam-policy-assignments-for-user, create-role-membership, delete-role-membership, list-role-memberships |
| Topics | [`topics.md`](topics.md) | create-topic, describe-topic, update-topic, delete-topic, list-topics, search-topics, describe-topic-permissions, update-topic-permissions, describe-topic-refresh, describe-topic-refresh-schedule, update-topic-refresh-schedule, list-topic-refresh-schedules, batch-create-topic-reviewed-answer, batch-delete-topic-reviewed-answer, list-topic-reviewed-answers |
| VPC Connections | [`vpc-connections.md`](vpc-connections.md) | create-vpc-connection, describe-vpc-connection, update-vpc-connection, delete-vpc-connection, list-vpc-connections |
| Embedding | [`embedding.md`](embedding.md) | generate-embed-url-for-registered-user, generate-embed-url-for-registered-user-with-identity, generate-embed-url-for-anonymous-user, get-dashboard-embed-url, get-session-embed-url |
| Asset Bundles | [`asset-bundles.md`](asset-bundles.md) | start-asset-bundle-export-job, describe-asset-bundle-export-job, list-asset-bundle-export-jobs, start-asset-bundle-import-job, describe-asset-bundle-import-job, list-asset-bundle-import-jobs |
| Brands | [`brands.md`](brands.md) | create-brand, describe-brand, update-brand, delete-brand, list-brands, describe-brand-assignment, update-brand-assignment, delete-brand-assignment, describe-brand-published-version, update-brand-published-version |
| Action Connectors | [`action-connectors.md`](action-connectors.md) | create-action-connector, describe-action-connector, update-action-connector, delete-action-connector, list-action-connectors, search-action-connectors, describe-action-connector-permissions, update-action-connector-permissions |
| Custom Permissions | [`custom-permissions.md`](custom-permissions.md) | create-custom-permissions, describe-custom-permissions, update-custom-permissions, delete-custom-permissions, list-custom-permissions, describe-account-custom-permission, update-account-custom-permission, delete-account-custom-permission, describe-role-custom-permission, update-role-custom-permission, delete-role-custom-permission, update-user-custom-permission, delete-user-custom-permission |
| Identity, Keys & Tags | [`identity-keys-tags.md`](identity-keys-tags.md) | describe-ip-restriction, update-ip-restriction, describe-key-registration, update-key-registration, list-identity-propagation-configs, update-identity-propagation-config, delete-identity-propagation-config, update-public-sharing-settings, get-identity-context, list-tags-for-resource, tag-resource, untag-resource |
| Flows | [`flows.md`](flows.md) | list-flows, search-flows, get-flow-metadata, get-flow-permissions, update-flow-permissions |
