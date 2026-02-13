# AWS CLI v2 — ECS (Elastic Container Service)

## Overview

Complete reference for all `aws ecs` subcommands in AWS CLI v2. Covers cluster management, service orchestration, task execution, task definition registration, container instance management, and capacity providers.

## Quick Reference — Common Workflows

### Create a cluster
```bash
aws ecs create-cluster --cluster-name my-cluster \
  --capacity-providers my-asg-cp \
  --default-capacity-provider-strategy capacityProvider=my-asg-cp,weight=1
```

### Register a task definition
```bash
aws ecs register-task-definition --cli-input-json file://task-def.json
```

### Create a service
```bash
aws ecs create-service --cluster my-cluster --service-name my-service \
  --task-definition my-task:1 --desired-count 2 \
  --launch-type EC2
```

### Run a standalone task
```bash
aws ecs run-task --cluster my-cluster --task-definition my-task:1 \
  --count 1 --launch-type EC2
```

### Update service (deploy new task def revision)
```bash
aws ecs update-service --cluster my-cluster --service-name my-service \
  --task-definition my-task:2
aws ecs wait services-stable --cluster my-cluster --services my-service
```

### List container instances and drain
```bash
aws ecs list-container-instances --cluster my-cluster --query 'containerInstanceArns'
aws ecs update-container-instances-state --cluster my-cluster \
  --container-instances arn:aws:ecs:... --status DRAINING
```

### Create capacity provider linked to ASG
```bash
aws ecs create-capacity-provider --name my-asg-cp \
  --auto-scaling-group-provider autoScalingGroupArn=arn:aws:autoscaling:...,managedScaling={status=ENABLED,targetCapacity=80},managedTerminationProtection=ENABLED
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Clusters | [`clusters.md`](clusters.md) | create-cluster, delete-cluster, describe-clusters, list-clusters, update-cluster, update-cluster-settings, put-cluster-capacity-providers |
| Services | [`services.md`](services.md) | create-service, delete-service, describe-services, list-services, update-service, update-service-primary-task-set |
| Tasks | [`tasks.md`](tasks.md) | run-task, start-task, stop-task, describe-tasks, list-tasks |
| Task Definitions | [`task-definitions.md`](task-definitions.md) | register-task-definition, deregister-task-definition, describe-task-definition, list-task-definitions, list-task-definition-families, delete-task-definitions |
| Container Instances | [`container-instances.md`](container-instances.md) | register-container-instance, deregister-container-instance, describe-container-instances, list-container-instances, update-container-instances-state, update-container-agent |
| Capacity Providers | [`capacity-providers.md`](capacity-providers.md) | create-capacity-provider, delete-capacity-provider, describe-capacity-providers, update-capacity-provider |
| Task Sets | [`task-sets.md`](task-sets.md) | create-task-set, delete-task-set, describe-task-sets, update-task-set |
| Account Settings | [`account-settings.md`](account-settings.md) | list-account-settings, put-account-setting, put-account-setting-default, delete-account-setting |
| Service Deployments | [`service-deployments.md`](service-deployments.md) | list-service-deployments, describe-service-deployments, describe-service-revisions |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| Attributes | [`attributes.md`](attributes.md) | put-attributes, delete-attributes, list-attributes |
| Execute Command | [`execute-command.md`](execute-command.md) | execute-command |
| Task Protection | [`task-protection.md`](task-protection.md) | get-task-protection, update-task-protection |
