# AWS CLI v2 — CodeDeploy

## Overview

Complete reference for all `aws deploy` subcommands in AWS CLI v2. Covers application management, deployment group configuration, deployment execution, deployment configurations, application revisions, on-premises instance management, and resource tagging.

> **Note:** The CLI service command is `aws deploy`, not `aws codedeploy`.

## Quick Reference — Common Workflows

### Create an application
```bash
aws deploy create-application --application-name my-app \
  --compute-platform Server
```

### Create a deployment group (EC2/on-premises)
```bash
aws deploy create-deployment-group \
  --application-name my-app \
  --deployment-group-name my-dg \
  --service-role-arn arn:aws:iam::123456789012:role/CodeDeployRole \
  --ec2-tag-filters Key=Name,Value=MyInstance,Type=KEY_AND_VALUE \
  --deployment-config-name CodeDeployDefault.OneAtATime
```

### Create a deployment group (ECS blue/green)
```bash
aws deploy create-deployment-group \
  --application-name my-ecs-app \
  --deployment-group-name my-ecs-dg \
  --service-role-arn arn:aws:iam::123456789012:role/CodeDeployECSRole \
  --deployment-style deploymentType=BLUE_GREEN,deploymentOption=WITH_TRAFFIC_CONTROL \
  --ecs-services serviceName=my-service,clusterName=my-cluster \
  --load-balancer-info targetGroupPairInfoList=[{targetGroups=[{name=tg-1},{name=tg-2}],prodTrafficRoute={listenerArns=[arn:aws:...]}]
```

### Create a deployment
```bash
aws deploy create-deployment \
  --application-name my-app \
  --deployment-group-name my-dg \
  --s3-location bucket=my-bucket,key=my-app.zip,bundleType=zip
```

### Get deployment status
```bash
aws deploy get-deployment --deployment-id d-XXXXXXXXX
```

### List deployments
```bash
aws deploy list-deployments --application-name my-app \
  --deployment-group-name my-dg \
  --include-only-statuses Succeeded Failed
```

### Stop a deployment
```bash
aws deploy stop-deployment --deployment-id d-XXXXXXXXX \
  --auto-rollback-enabled
```

### Register an on-premises instance
```bash
aws deploy register-on-premises-instance \
  --instance-name my-onprem-instance \
  --iam-user-arn arn:aws:iam::123456789012:user/OnPremUser
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Applications | [`applications.md`](applications.md) | create-application, delete-application, get-application, list-applications, update-application, batch-get-applications |
| Deployment Groups | [`deployment-groups.md`](deployment-groups.md) | create-deployment-group, delete-deployment-group, get-deployment-group, list-deployment-groups, update-deployment-group, batch-get-deployment-groups |
| Deployments | [`deployments.md`](deployments.md) | create-deployment, get-deployment, list-deployments, stop-deployment, batch-get-deployments, continue-deployment |
| Deployment Configs | [`deployment-configs.md`](deployment-configs.md) | create-deployment-config, delete-deployment-config, get-deployment-config, list-deployment-configs |
| Revisions | [`revisions.md`](revisions.md) | register-application-revision, get-application-revision, list-application-revisions, batch-get-application-revisions |
| Instances | [`instances.md`](instances.md) | register-on-premises-instance, deregister-on-premises-instance, get-on-premises-instance, list-on-premises-instances, batch-get-on-premises-instances, add-tags-to-on-premises-instances, remove-tags-from-on-premises-instances |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
