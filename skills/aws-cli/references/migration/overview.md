# AWS CLI v2 — Migration (MGN + Migration Hub Config + Migration Hub Orchestrator)

## Overview

Complete reference for AWS migration services in AWS CLI v2. Covers the Application Migration Service (MGN) for lift-and-shift migrations, Migration Hub Config for home region management, and Migration Hub Orchestrator for workflow-based migrations. MGN automates the replication, testing, and cutover of source servers to AWS EC2 instances.

## Quick Reference — Common Workflows

### Initialize the MGN service
```bash
aws mgn initialize-service
```

### Discover and monitor source servers
```bash
# List all source servers
aws mgn describe-source-servers

# Filter by lifecycle state
aws mgn describe-source-servers \
  --filters '{"lifeCycleStates": ["READY_FOR_TEST"]}'
```

### Configure replication
```bash
# Create a replication configuration template
aws mgn create-replication-configuration-template \
  --replication-server-instance-type m5.xlarge \
  --use-dedicated-replication-server \
  --default-large-staging-disk-type GP3 \
  --ebs-encryption DEFAULT \
  --data-plane-routing PRIVATE_IP \
  --staging-area-subnet-id subnet-0abc123 \
  --staging-area-tags Environment=staging \
  --replication-servers-security-groups-i-ds sg-0abc123 \
  --bandwidth-throttling 0

# Update replication configuration for a source server
aws mgn update-replication-configuration \
  --source-server-id s-abc123def456 \
  --replication-server-instance-type m5.xlarge \
  --staging-area-subnet-id subnet-0abc123
```

### Test and cutover workflow
```bash
# Start a test launch
aws mgn start-test --source-server-ids s-abc123def456

# Finalize cutover after verification
aws mgn start-cutover --source-server-ids s-abc123def456

# After cutover is complete, finalize
aws mgn finalize-cutover --source-server-id s-abc123def456
```

### Organize with waves and applications
```bash
# Create a wave for grouping migrations
aws mgn create-wave --name "Wave 1 - Web Servers"

# Create an application
aws mgn create-application --name "E-commerce Platform"

# Associate servers to application
aws mgn associate-source-servers \
  --application-id app-abc123 \
  --source-server-ids s-abc123 s-def456
```

### Set Migration Hub home region
```bash
aws migrationhub-config create-home-region-control \
  --home-region us-west-2 \
  --target Type=ACCOUNT,Id=123456789012
```

### Create an orchestrated migration workflow
```bash
aws migrationhuborchestrator create-workflow \
  --name "SAP Migration" \
  --template-id template-abc123 \
  --application-configuration-id app-abc123 \
  --input-parameters '{"key": "value"}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Source Servers | [`source-servers.md`](source-servers.md) | describe-source-servers, delete-source-server, update-source-server, update-source-server-replication-type, change-server-life-cycle-state, mark-as-archived, disconnect-from-service, describe-vcenter-clients, delete-vcenter-client |
| Replication | [`replication.md`](replication.md) | create-replication-configuration-template, delete-replication-configuration-template, describe-replication-configuration-templates, update-replication-configuration-template, get-replication-configuration, update-replication-configuration, start-replication, stop-replication, pause-replication, resume-replication, retry-data-replication |
| Launch Config | [`launch-config.md`](launch-config.md) | create-launch-configuration-template, delete-launch-configuration-template, describe-launch-configuration-templates, update-launch-configuration-template, get-launch-configuration, update-launch-configuration |
| Cutover | [`cutover.md`](cutover.md) | start-test, start-cutover, finalize-cutover, terminate-target-instances |
| Waves & Applications | [`waves-applications.md`](waves-applications.md) | create-wave, delete-wave, list-waves, update-wave, archive-wave, unarchive-wave, create-application, delete-application, list-applications, update-application, archive-application, unarchive-application, associate-applications, disassociate-applications, associate-source-servers, disassociate-source-servers |
| Connectors | [`connectors.md`](connectors.md) | create-connector, delete-connector, list-connectors, update-connector |
| Actions | [`actions.md`](actions.md) | put-source-server-action, remove-source-server-action, list-source-server-actions, put-template-action, remove-template-action, list-template-actions |
| Jobs | [`jobs.md`](jobs.md) | describe-jobs, describe-job-log-items, delete-job |
| Import & Export | [`import-export.md`](import-export.md) | start-import, list-imports, list-import-errors, start-export, list-exports, list-export-errors |
| Migration Hub Config | [`migrationhub-config.md`](migrationhub-config.md) | create-home-region-control, delete-home-region-control, describe-home-region-controls, get-home-region |
| Orchestrator Workflows | [`orchestrator-workflows.md`](orchestrator-workflows.md) | create-workflow, delete-workflow, get-workflow, list-workflows, update-workflow, start-workflow, stop-workflow |
| Orchestrator Steps | [`orchestrator-steps.md`](orchestrator-steps.md) | create-workflow-step, delete-workflow-step, get-workflow-step, list-workflow-steps, update-workflow-step, retry-workflow-step, create-workflow-step-group, delete-workflow-step-group, get-workflow-step-group, list-workflow-step-groups, update-workflow-step-group |
| Orchestrator Templates | [`orchestrator-templates.md`](orchestrator-templates.md) | create-template, delete-template, get-template, list-templates, update-template, get-template-step, list-template-steps, get-template-step-group, list-template-step-groups, list-plugins |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource, initialize-service, list-managed-accounts |
