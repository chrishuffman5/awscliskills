# AWS CLI v2 — Redshift (Amazon Redshift + Redshift Data API + Redshift Serverless)

## Overview

Complete reference for `aws redshift`, `aws redshift-data`, and `aws redshift-serverless` subcommands in AWS CLI v2. Covers provisioned cluster management, snapshot operations, parameter groups, security and networking, data sharing, scheduled actions, event subscriptions and logging, Identity Center authentication, HSM configuration, reserved nodes, the Redshift Data API for running queries without managing connections, and Redshift Serverless namespaces, workgroups, and serverless snapshots.

## Quick Reference — Common Workflows

### Create a provisioned cluster
```bash
aws redshift create-cluster --cluster-identifier my-cluster \
  --node-type ra3.xlplus --number-of-nodes 2 \
  --master-username admin --master-user-password 'MyP@ssw0rd!' \
  --db-name mydb
```

### Describe cluster status
```bash
aws redshift describe-clusters --cluster-identifier my-cluster \
  --query 'Clusters[0].{Status:ClusterStatus,Endpoint:Endpoint}'
```

### Take a manual snapshot
```bash
aws redshift create-cluster-snapshot \
  --cluster-identifier my-cluster \
  --snapshot-identifier my-manual-snap
```

### Restore a cluster from snapshot
```bash
aws redshift restore-from-cluster-snapshot \
  --cluster-identifier my-restored-cluster \
  --snapshot-identifier my-manual-snap
```

### Run a SQL query via the Data API
```bash
aws redshift-data execute-statement \
  --cluster-identifier my-cluster \
  --database mydb --db-user admin \
  --sql "SELECT * FROM pg_catalog.pg_tables LIMIT 10"
```

### Get Data API query results
```bash
aws redshift-data describe-statement --id <statement-id>
aws redshift-data get-statement-result --id <statement-id>
```

### Create a Redshift Serverless namespace and workgroup
```bash
aws redshift-serverless create-namespace \
  --namespace-name my-ns --db-name mydb --admin-username admin \
  --admin-user-password 'MyP@ssw0rd!'

aws redshift-serverless create-workgroup \
  --workgroup-name my-wg --namespace-name my-ns \
  --base-capacity 32
```

### Resize a provisioned cluster
```bash
aws redshift resize-cluster --cluster-identifier my-cluster \
  --cluster-type multi-node --node-type ra3.xlplus --number-of-nodes 4
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Clusters | [`clusters.md`](clusters.md) | create-cluster, delete-cluster, describe-clusters, modify-cluster, reboot-cluster, resize-cluster, pause-cluster, resume-cluster, restore-from-cluster-snapshot |
| Snapshots | [`snapshots.md`](snapshots.md) | create-cluster-snapshot, delete-cluster-snapshot, describe-cluster-snapshots, copy-cluster-snapshot, modify-cluster-snapshot-attribute, authorize-snapshot-access, revoke-snapshot-access, batch-delete-cluster-snapshots, modify-snapshot-copy-retention-period, enable-snapshot-copy, disable-snapshot-copy, modify-cluster-snapshot-schedule, create-snapshot-schedule, delete-snapshot-schedule, describe-snapshot-schedules, modify-snapshot-schedule, create-snapshot-copy-grant, delete-snapshot-copy-grant, describe-snapshot-copy-grants |
| Parameter Groups | [`parameter-groups.md`](parameter-groups.md) | create-cluster-parameter-group, delete-cluster-parameter-group, describe-cluster-parameter-groups, describe-cluster-parameters, modify-cluster-parameter-group, reset-cluster-parameter-group, describe-default-cluster-parameters |
| Security & Networking | [`security-networking.md`](security-networking.md) | create-cluster-security-group, delete-cluster-security-group, describe-cluster-security-groups, authorize-cluster-security-group-ingress, revoke-cluster-security-group-ingress, create-cluster-subnet-group, delete-cluster-subnet-group, describe-cluster-subnet-groups, modify-cluster-subnet-group, modify-cluster-iam-roles, create-endpoint-access, delete-endpoint-access, describe-endpoint-access, modify-endpoint-access, create-authentication-profile, delete-authentication-profile, describe-authentication-profiles, modify-cluster-maintenance |
| Data Sharing | [`data-sharing.md`](data-sharing.md) | create-data-share, delete-data-share, describe-data-shares, describe-data-shares-for-consumer, describe-data-shares-for-producer, associate-data-share-consumer, disassociate-data-share-consumer, authorize-data-share, deauthorize-data-share |
| Scheduled Actions | [`scheduled-actions.md`](scheduled-actions.md) | create-scheduled-action, delete-scheduled-action, describe-scheduled-actions, modify-scheduled-action |
| Events & Logging | [`events-logging.md`](events-logging.md) | create-event-subscription, delete-event-subscription, describe-event-subscriptions, modify-event-subscription, describe-events, describe-event-categories, enable-logging, disable-logging, describe-logging-status |
| Integrations | [`integrations.md`](integrations.md) | create-integration, delete-integration, describe-integrations, modify-integration, create-redshift-idc-application, delete-redshift-idc-application, describe-redshift-idc-applications, modify-redshift-idc-application |
| IDC Authentication | [`idc-auth.md`](idc-auth.md) | create-redshift-idc-application, delete-redshift-idc-application, describe-redshift-idc-applications, modify-redshift-idc-application |
| HSM | [`hsm.md`](hsm.md) | create-hsm-client-certificate, delete-hsm-client-certificate, describe-hsm-client-certificates, create-hsm-configuration, delete-hsm-configuration, describe-hsm-configurations |
| Reserved Nodes | [`reserved-nodes.md`](reserved-nodes.md) | describe-reserved-nodes, describe-reserved-node-offerings, purchase-reserved-node-offering, accept-reserved-node-exchange, describe-reserved-node-exchange-status, get-reserved-node-exchange-offerings, get-reserved-node-exchange-configuration-options |
| Partners & Tags | [`partners-tags.md`](partners-tags.md) | add-partner, delete-partner, describe-partners, create-tags, delete-tags, describe-tags |
| Data API | [`data-api.md`](data-api.md) | execute-statement, batch-execute-statement, cancel-statement, describe-statement, get-statement-result, list-statements, list-databases, list-schemas, list-tables, describe-table |
| Serverless Namespaces | [`serverless-namespaces.md`](serverless-namespaces.md) | create-namespace, delete-namespace, get-namespace, list-namespaces, update-namespace |
| Serverless Workgroups | [`serverless-workgroups.md`](serverless-workgroups.md) | create-workgroup, delete-workgroup, get-workgroup, list-workgroups, update-workgroup, get-endpoint-access, create-endpoint-access, delete-endpoint-access, list-endpoint-access, update-endpoint-access |
| Serverless Snapshots | [`serverless-snapshots.md`](serverless-snapshots.md) | create-snapshot, delete-snapshot, get-snapshot, list-snapshots, update-snapshot, restore-from-snapshot, convert-recovery-point-to-snapshot, get-recovery-point, list-recovery-points, restore-table-from-snapshot |
| Serverless Scheduling | [`serverless-scheduling.md`](serverless-scheduling.md) | create-scheduled-action, delete-scheduled-action, get-scheduled-action, list-scheduled-actions, update-scheduled-action |
| Serverless Domains & Tags | [`serverless-domains-tags.md`](serverless-domains-tags.md) | create-custom-domain-association, delete-custom-domain-association, get-custom-domain-association, list-custom-domain-associations, update-custom-domain-association, tag-resource, untag-resource, list-tags-for-resource, get-credentials, get-table-restore-status, list-table-restore-status |
| Wait Commands | [`wait.md`](wait.md) | wait cluster-available, wait cluster-deleted, wait cluster-restored, wait snapshot-available |
