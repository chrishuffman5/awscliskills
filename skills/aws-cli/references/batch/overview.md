# AWS CLI v2 — Batch

## Overview

Complete reference for all `aws batch` subcommands in AWS CLI v2. Covers job submission and management, job definitions, job queues, compute environments, scheduling policies, consumable resources, service environments, and tagging.

## Quick Reference — Common Workflows

### Create a compute environment
```bash
aws batch create-compute-environment \
  --compute-environment-name my-ce \
  --type MANAGED \
  --compute-resources type=EC2,minvCpus=0,maxvCpus=256,desiredvCpus=0,instanceTypes=optimal,subnets=subnet-abc123,securityGroupIds=sg-abc123,instanceRole=ecsInstanceRole
```

### Create a job queue
```bash
aws batch create-job-queue --job-queue-name my-queue \
  --priority 1 \
  --compute-environment-order order=1,computeEnvironment=my-ce
```

### Register a job definition
```bash
aws batch register-job-definition \
  --job-definition-name my-job-def \
  --type container \
  --container-properties '{"image":"my-image:latest","vcpus":1,"memory":512}'
```

### Submit a job
```bash
aws batch submit-job --job-name my-job \
  --job-queue my-queue \
  --job-definition my-job-def
```

### List and describe jobs
```bash
aws batch list-jobs --job-queue my-queue --job-status RUNNING
aws batch describe-jobs --jobs job-id-1 job-id-2
```

### Cancel or terminate a job
```bash
aws batch cancel-job --job-id abc-123 --reason "No longer needed"
aws batch terminate-job --job-id abc-123 --reason "Timeout exceeded"
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Jobs | [`jobs.md`](jobs.md) | submit-job, cancel-job, terminate-job, describe-jobs, list-jobs, get-job-queue-snapshot |
| Job Definitions | [`job-definitions.md`](job-definitions.md) | register-job-definition, deregister-job-definition, describe-job-definitions |
| Job Queues | [`job-queues.md`](job-queues.md) | create-job-queue, update-job-queue, delete-job-queue, describe-job-queues |
| Compute Environments | [`compute-environments.md`](compute-environments.md) | create-compute-environment, update-compute-environment, delete-compute-environment, describe-compute-environments |
| Scheduling Policies | [`scheduling-policies.md`](scheduling-policies.md) | create-scheduling-policy, update-scheduling-policy, delete-scheduling-policy, describe-scheduling-policies, list-scheduling-policies |
| Consumable Resources | [`consumable-resources.md`](consumable-resources.md) | create-consumable-resource, update-consumable-resource, delete-consumable-resource, describe-consumable-resource, list-consumable-resources, list-jobs-by-consumable-resource |
| Service Environments | [`service-environments.md`](service-environments.md) | create-service-environment, update-service-environment, delete-service-environment, describe-service-environments, describe-service-job, submit-service-job, list-service-jobs, terminate-service-job |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
