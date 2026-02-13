# AWS CLI v2 — CloudFormation

## Overview

Complete reference for all `aws cloudformation` subcommands in AWS CLI v2. Covers stack lifecycle management, change sets, stack sets for multi-account/multi-region deployments, drift detection, resource imports, stack refactors, generated templates, resource scanning, type registry, exports/imports, organization integrations, hooks, and wait commands.

## Quick Reference — Common Workflows

### Create a stack
```bash
aws cloudformation create-stack --stack-name my-stack \
  --template-body file://template.yaml \
  --parameters ParameterKey=Env,ParameterValue=prod \
  --capabilities CAPABILITY_NAMED_IAM \
  --tags Key=Project,Value=MyApp
```

### Update a stack
```bash
aws cloudformation update-stack --stack-name my-stack \
  --template-body file://template.yaml \
  --parameters ParameterKey=Env,ParameterValue=staging \
  --capabilities CAPABILITY_NAMED_IAM
aws cloudformation wait stack-update-complete --stack-name my-stack
```

### Create and execute a change set
```bash
aws cloudformation create-change-set --stack-name my-stack \
  --change-set-name my-changes --template-body file://template.yaml \
  --capabilities CAPABILITY_NAMED_IAM
aws cloudformation wait change-set-create-complete \
  --stack-name my-stack --change-set-name my-changes
aws cloudformation describe-change-set --stack-name my-stack \
  --change-set-name my-changes
aws cloudformation execute-change-set --stack-name my-stack \
  --change-set-name my-changes
```

### Delete a stack
```bash
aws cloudformation delete-stack --stack-name my-stack
aws cloudformation wait stack-delete-complete --stack-name my-stack
```

### Detect drift on a stack
```bash
aws cloudformation detect-stack-drift --stack-name my-stack
aws cloudformation describe-stack-drift-detection-status \
  --stack-drift-detection-id <detection-id>
aws cloudformation describe-stack-resource-drifts --stack-name my-stack
```

### Create a stack set (multi-account deployment)
```bash
aws cloudformation create-stack-set --stack-set-name my-set \
  --template-body file://template.yaml \
  --permission-model SERVICE_MANAGED \
  --auto-deployment Enabled=true,RetainStacksOnAccountRemoval=false
aws cloudformation create-stack-instances --stack-set-name my-set \
  --deployment-targets OrganizationalUnitIds=ou-1234 \
  --regions us-east-1 us-west-2
```

### Import existing resources into a stack
```bash
aws cloudformation create-change-set --stack-name my-stack \
  --change-set-name import-resources --change-set-type IMPORT \
  --resources-to-import file://resources-to-import.json \
  --template-body file://template.yaml
```

### List exports and check cross-stack references
```bash
aws cloudformation list-exports --query 'Exports[].{Name:Name,Value:Value}'
aws cloudformation list-imports --export-name my-export
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Stacks | [`stacks.md`](stacks.md) | create-stack, update-stack, delete-stack, describe-stacks, list-stacks, list-stack-resources, describe-stack-resources, describe-stack-resource, describe-stack-events, cancel-update-stack, continue-update-rollback, rollback-stack, update-termination-protection, signal-resource, get-stack-policy, set-stack-policy, get-template, get-template-summary, estimate-template-cost, validate-template, deploy, package |
| Change Sets | [`change-sets.md`](change-sets.md) | create-change-set, delete-change-set, describe-change-set, describe-change-set-hooks, execute-change-set, list-change-sets |
| Stack Sets | [`stack-sets.md`](stack-sets.md) | create-stack-set, update-stack-set, delete-stack-set, describe-stack-set, describe-stack-set-operation, list-stack-sets, list-stack-set-operations, list-stack-set-operation-results, list-stack-instances, describe-stack-instance, create-stack-instances, update-stack-instances, delete-stack-instances, import-stacks-to-stack-set, stop-stack-set-operation |
| Drift Detection | [`drift-detection.md`](drift-detection.md) | detect-stack-drift, detect-stack-resource-drift, detect-stack-set-drift, describe-stack-drift-detection-status, describe-stack-resource-drifts |
| Stack Refactors | [`stack-refactors.md`](stack-refactors.md) | create-stack-refactor, describe-stack-refactor, execute-stack-refactor, list-stack-refactors, list-stack-refactor-actions |
| Generated Templates | [`generated-templates.md`](generated-templates.md) | create-generated-template, update-generated-template, delete-generated-template, describe-generated-template, get-generated-template, list-generated-templates |
| Resource Scanning | [`resource-scanning.md`](resource-scanning.md) | start-resource-scan, describe-resource-scan, list-resource-scans, list-resource-scan-resources, list-resource-scan-related-resources |
| Type Registry | [`type-registry.md`](type-registry.md) | register-type, deregister-type, describe-type, describe-type-registration, list-types, list-type-versions, list-type-registrations, set-type-default-version, set-type-configuration, batch-describe-type-configurations, activate-type, deactivate-type, publish-type, test-type, register-publisher, describe-publisher, record-handler-progress |
| Exports & Imports | [`exports-imports.md`](exports-imports.md) | list-exports, list-imports, describe-account-limits |
| Organizations | [`organizations.md`](organizations.md) | activate-organizations-access, deactivate-organizations-access, describe-organizations-access |
| Hooks | [`hooks.md`](hooks.md) | list-hook-results, get-hook-result |
| Wait Commands | [`wait.md`](wait.md) | wait stack-create-complete, wait stack-update-complete, wait stack-delete-complete, wait stack-exists, wait stack-import-complete, wait stack-rollback-complete, wait change-set-create-complete, wait type-registration-complete |
