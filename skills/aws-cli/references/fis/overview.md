# AWS CLI v2 — FIS (Fault Injection Service)

## Overview

Complete reference for all `aws fis` subcommands in AWS CLI v2. Covers experiment templates, experiments, actions, target resource types, target account configurations, safety levers, and tagging.

## Quick Reference — Common Workflows

### Create an experiment template
```bash
aws fis create-experiment-template \
  --description "Stop EC2 instances" \
  --role-arn arn:aws:iam::123456789012:role/FISRole \
  --stop-conditions '[{"source":"none"}]' \
  --actions '{"stop-instances":{"actionId":"aws:ec2:stop-instances","parameters":{"startInstancesAfterDuration":"PT5M"},"targets":{"Instances":"my-instances"}}}' \
  --targets '{"my-instances":{"resourceType":"aws:ec2:instance","selectionMode":"ALL","resourceTags":{"env":["test"]}}}' \
  --tags Environment=test
```

### List experiment templates
```bash
aws fis list-experiment-templates
```

### Start an experiment
```bash
aws fis start-experiment \
  --experiment-template-id EXT123abc \
  --tags RunBy=chaos-team
```

### Monitor an experiment
```bash
aws fis get-experiment --id EXP123abc
```

### Stop an experiment
```bash
aws fis stop-experiment --id EXP123abc
```

### List available actions
```bash
aws fis list-actions
```

### List target resource types
```bash
aws fis list-target-resource-types
```

### Check safety lever state
```bash
aws fis get-safety-lever \
  --id arn:aws:fis:us-east-1:123456789012:safety-lever/default
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Experiment Templates | [`experiment-templates.md`](experiment-templates.md) | create-experiment-template, delete-experiment-template, get-experiment-template, list-experiment-templates, update-experiment-template |
| Experiments | [`experiments.md`](experiments.md) | start-experiment, stop-experiment, get-experiment, list-experiments, list-experiment-resolved-targets |
| Actions & Resources | [`actions-resources.md`](actions-resources.md) | get-action, list-actions, get-target-resource-type, list-target-resource-types |
| Target Accounts | [`target-accounts.md`](target-accounts.md) | create-target-account-configuration, delete-target-account-configuration, get-target-account-configuration, list-target-account-configurations, update-target-account-configuration, get-experiment-target-account-configuration, list-experiment-target-account-configurations |
| Safety | [`safety.md`](safety.md) | get-safety-lever, update-safety-lever-state |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
