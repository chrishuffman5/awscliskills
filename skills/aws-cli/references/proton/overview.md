# AWS CLI v2 — Proton

## Overview

Complete reference for all `aws proton` subcommands in AWS CLI v2. Covers environment and service management, templates, components, account connections, repository sync, and tagging for AWS Proton — a managed deployment service for container and serverless applications.

## Quick Reference — Common Workflows

### Create an environment template
```bash
aws proton create-environment-template --name my-env-template \
  --display-name "My Environment" --description "Production environment"
aws proton create-environment-template-version --template-name my-env-template \
  --source s3="{bucket=my-bucket,key=env-template.tar.gz}"
```

### Create an environment
```bash
aws proton create-environment --name my-env \
  --template-name my-env-template --template-major-version 1 \
  --spec file://env-spec.yaml \
  --proton-service-role-arn arn:aws:iam::123456789012:role/ProtonServiceRole
aws proton wait environment-deployed --name my-env
```

### Create a service template and service
```bash
aws proton create-service-template --name my-svc-template
aws proton create-service-template-version --template-name my-svc-template \
  --compatible-environment-templates "[{templateName=my-env-template,majorVersion=1}]" \
  --source s3="{bucket=my-bucket,key=svc-template.tar.gz}"
aws proton create-service --name my-service \
  --template-name my-svc-template --template-major-version 1 \
  --spec file://svc-spec.yaml
aws proton wait service-created --name my-service
```

### Update a service instance
```bash
aws proton update-service-instance --name my-instance \
  --service-name my-service --deployment-type CURRENT_VERSION \
  --spec file://instance-spec.yaml
aws proton wait service-instance-deployed --name my-instance \
  --service-name my-service
```

### Delete a service and environment
```bash
aws proton delete-service --name my-service
aws proton wait service-deleted --name my-service
aws proton delete-environment --name my-env
aws proton wait environment-deployed --name my-env
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Environments | [`environments.md`](environments.md) | create-environment, update-environment, delete-environment, get-environment, list-environments, cancel-environment-deployment, list-environment-outputs, list-environment-provisioned-resources |
| Environment Templates | [`environment-templates.md`](environment-templates.md) | create-environment-template, update-environment-template, delete-environment-template, get-environment-template, list-environment-templates, create-environment-template-version, update-environment-template-version, delete-environment-template-version, get-environment-template-version, list-environment-template-versions |
| Services | [`services.md`](services.md) | create-service, update-service, delete-service, get-service, list-services |
| Service Instances | [`service-instances.md`](service-instances.md) | update-service-instance, get-service-instance, list-service-instances, list-service-instance-outputs, list-service-instance-provisioned-resources |
| Service Templates | [`service-templates.md`](service-templates.md) | create-service-template, update-service-template, delete-service-template, get-service-template, list-service-templates, create-service-template-version, update-service-template-version, delete-service-template-version, get-service-template-version, list-service-template-versions |
| Components | [`components.md`](components.md) | create-component, update-component, delete-component, get-component, list-components, cancel-component-deployment, list-component-outputs, list-component-provisioned-resources |
| Account Connections | [`account-connections.md`](account-connections.md) | create-environment-account-connection, update-environment-account-connection, delete-environment-account-connection, get-environment-account-connection, list-environment-account-connections, accept-environment-account-connection, reject-environment-account-connection |
| Repositories & Sync | [`repositories-sync.md`](repositories-sync.md) | create-repository, delete-repository, get-repository, list-repositories, get-repository-sync-status, create-template-sync-config, update-template-sync-config, delete-template-sync-config, get-template-sync-config, get-template-sync-status, create-service-sync-config, update-service-sync-config, delete-service-sync-config, get-service-sync-config, get-service-sync-blocker-summary, notify-resource-deployment-status-change |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| Wait Commands | [`wait.md`](wait.md) | wait environment-deployed, wait environment-template-version-registered, wait service-created, wait service-deleted, wait service-updated, wait service-instance-deployed, wait service-pipeline-deployed, wait service-template-version-registered, wait component-deployed, wait component-deleted |
