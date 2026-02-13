# AWS CLI v2 — Systems Manager (SSM)

## Overview

Complete reference for all `aws ssm` subcommands in AWS CLI v2. Covers Parameter Store, Documents, Run Command, Session Manager, Maintenance Windows, Patch Manager, State Manager, Inventory, OpsItems, and resource tagging.

## Quick Reference — Common Workflows

### Store a parameter
```bash
aws ssm put-parameter --name /app/db-host --value mydb.example.com \
  --type String --overwrite
```

### Store a secure parameter
```bash
aws ssm put-parameter --name /app/db-password --value secret123 \
  --type SecureString --key-id alias/my-key
```

### Get a parameter value
```bash
aws ssm get-parameter --name /app/db-host --query 'Parameter.Value' --output text
aws ssm get-parameter --name /app/db-password --with-decryption --query 'Parameter.Value'
```

### Get parameters by path
```bash
aws ssm get-parameters-by-path --path /app/ --recursive --with-decryption
```

### Run a command on instances
```bash
aws ssm send-command --document-name AWS-RunShellScript \
  --targets Key=tag:Environment,Values=Production \
  --parameters commands=["uptime","df -h"]
```

### Start an interactive session
```bash
aws ssm start-session --target i-0123456789abcdef0
```

### Create a maintenance window
```bash
aws ssm create-maintenance-window --name my-window \
  --schedule "cron(0 2 ? * SUN *)" --duration 3 --cutoff 1 \
  --allow-unassociated-targets
```

### Create a patch baseline
```bash
aws ssm create-patch-baseline --name my-baseline \
  --operating-system AMAZON_LINUX_2 \
  --approval-rules "PatchRules=[{PatchFilterGroup={PatchFilters=[{Key=SEVERITY,Values=[Critical,Important]}]},ApproveAfterDays=7}]"
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Parameter Store | [`parameter-store.md`](parameter-store.md) | put-parameter, get-parameter, get-parameters, get-parameters-by-path, delete-parameter, delete-parameters, describe-parameters, get-parameter-history, label-parameter-version, unlabel-parameter-version |
| Documents | [`documents.md`](documents.md) | create-document, delete-document, describe-document, get-document, list-documents, update-document, update-document-default-version, list-document-versions |
| Run Command | [`run-command.md`](run-command.md) | send-command, list-commands, list-command-invocations, get-command-invocation, cancel-command |
| Session Manager | [`session-manager.md`](session-manager.md) | start-session, terminate-session, describe-sessions, resume-session |
| Maintenance Windows | [`maintenance-windows.md`](maintenance-windows.md) | create-maintenance-window, delete-maintenance-window, describe-maintenance-windows, get-maintenance-window, update-maintenance-window, register-target-with-maintenance-window, deregister-target-from-maintenance-window, describe-maintenance-window-targets, register-task-with-maintenance-window, deregister-task-from-maintenance-window, describe-maintenance-window-tasks, describe-maintenance-window-executions, get-maintenance-window-execution, get-maintenance-window-execution-task |
| Patch Baselines | [`patch-baselines.md`](patch-baselines.md) | create-patch-baseline, delete-patch-baseline, describe-patch-baselines, get-patch-baseline, update-patch-baseline, register-patch-baseline-for-patch-group, deregister-patch-baseline-for-patch-group, describe-patch-groups, describe-patch-group-state, describe-instance-patch-states, describe-instance-patches |
| State Manager | [`state-manager.md`](state-manager.md) | create-association, delete-association, describe-association, list-associations, update-association, describe-association-executions, describe-association-execution-targets |
| Inventory | [`inventory.md`](inventory.md) | put-inventory, get-inventory, get-inventory-schema, list-inventory-entries, delete-inventory |
| OpsItems | [`ops-items.md`](ops-items.md) | create-ops-item, delete-ops-item, get-ops-item, list-ops-item-events, update-ops-item, describe-ops-items, create-ops-metadata, delete-ops-metadata, get-ops-metadata, list-ops-metadata, update-ops-metadata |
| Tags | [`tags.md`](tags.md) | add-tags-to-resource, remove-tags-from-resource, list-tags-for-resource |
