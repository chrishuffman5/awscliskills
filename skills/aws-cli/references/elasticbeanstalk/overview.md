# AWS CLI v2 — Elastic Beanstalk

## Overview

Complete reference for all `aws elasticbeanstalk` subcommands in AWS CLI v2. Covers application management, application version lifecycle, environment creation and configuration, managed actions, configuration templates and option settings, custom platform management, operational roles, and utility commands. AWS Elastic Beanstalk handles capacity provisioning, load balancing, scaling, and health monitoring for web applications and services.

## Quick Reference — Common Workflows

### Create an application
```bash
aws elasticbeanstalk create-application --application-name my-app \
  --description "My web application"
```

### Create an application version from S3
```bash
aws elasticbeanstalk create-application-version \
  --application-name my-app \
  --version-label v1.0.0 \
  --source-bundle S3Bucket=my-bucket,S3Key=app-v1.0.0.zip
```

### Create an environment
```bash
aws elasticbeanstalk create-environment \
  --application-name my-app \
  --environment-name my-app-prod \
  --solution-stack-name "64bit Amazon Linux 2023 v6.1.0 running Node.js 20" \
  --version-label v1.0.0 \
  --option-settings Namespace=aws:autoscaling:launchconfiguration,OptionName=InstanceType,Value=t3.medium
```

### Deploy a new version to an environment
```bash
aws elasticbeanstalk update-environment \
  --environment-name my-app-prod \
  --version-label v2.0.0
```

### Check environment health
```bash
aws elasticbeanstalk describe-environment-health \
  --environment-name my-app-prod \
  --attribute-names All
```

### List available solution stacks
```bash
aws elasticbeanstalk list-available-solution-stacks \
  --query 'SolutionStacks[?contains(@,`Node.js`)]'
```

### Terminate an environment
```bash
aws elasticbeanstalk terminate-environment --environment-name my-app-prod
aws elasticbeanstalk wait environment-terminated --environment-names my-app-prod
```

### Swap environment CNAMEs (blue/green)
```bash
aws elasticbeanstalk swap-environment-cnames \
  --source-environment-name my-app-blue \
  --destination-environment-name my-app-green
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Applications | [`applications.md`](applications.md) | create-application, describe-applications, update-application, delete-application |
| Application Versions | [`application-versions.md`](application-versions.md) | create-application-version, describe-application-versions, update-application-version, delete-application-version |
| Environments | [`environments.md`](environments.md) | create-environment, describe-environments, update-environment, terminate-environment, rebuild-environment, restart-app-server, describe-environment-health, describe-instances-health, compose-environments, swap-environment-cnames, abort-environment-update, describe-environment-resources, list-available-solution-stacks |
| Managed Actions | [`managed-actions.md`](managed-actions.md) | describe-environment-managed-actions, describe-environment-managed-action-history, apply-environment-managed-action |
| Configuration | [`configuration.md`](configuration.md) | create-configuration-template, describe-configuration-settings, update-configuration-template, delete-configuration-template, describe-configuration-options, validate-configuration-settings |
| Platforms | [`platforms.md`](platforms.md) | create-platform-version, describe-platform-version, list-platform-versions, list-platform-branches, delete-platform-version |
| Operations & Roles | [`operations-roles.md`](operations-roles.md) | describe-events, describe-account-attributes, create-storage-location, associate-environment-operations-role, disassociate-environment-operations-role |
| Utility | [`utility.md`](utility.md) | check-dns-availability, request-environment-info, retrieve-environment-info, list-tags-for-resource, update-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait environment-exists, wait environment-terminated, wait environment-updated |
