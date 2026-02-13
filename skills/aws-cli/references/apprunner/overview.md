# AWS CLI v2 — App Runner

## Overview

Complete reference for all `aws apprunner` subcommands in AWS CLI v2. Covers service creation and management, source code and image connections, auto scaling configurations, observability configurations, VPC connectors and ingress, custom domain associations, and tagging. AWS App Runner is a fully managed service for building, deploying, and running containerized web applications and APIs at scale.

## Quick Reference — Common Workflows

### Create a service from a container image
```bash
aws apprunner create-service --service-name my-api \
  --source-configuration '{
    "ImageRepository": {
      "ImageIdentifier": "123456789012.dkr.ecr.us-east-1.amazonaws.com/my-app:latest",
      "ImageRepositoryType": "ECR",
      "ImageConfiguration": {"Port": "8080"}
    },
    "AutoDeploymentsEnabled": true,
    "AuthenticationConfiguration": {"AccessRoleArn": "arn:aws:iam::123456789012:role/AppRunnerECRAccess"}
  }'
```

### Create a service from source code
```bash
aws apprunner create-service --service-name my-web-app \
  --source-configuration '{
    "CodeRepository": {
      "RepositoryUrl": "https://github.com/my-org/my-app",
      "SourceCodeVersion": {"Type": "BRANCH", "Value": "main"},
      "CodeConfiguration": {
        "ConfigurationSource": "API",
        "CodeConfigurationValues": {"Runtime": "NODEJS_18", "BuildCommand": "npm install", "StartCommand": "npm start", "Port": "8080"}
      }
    },
    "AutoDeploymentsEnabled": true,
    "AuthenticationConfiguration": {"ConnectionArn": "arn:aws:apprunner:us-east-1:123456789012:connection/my-conn/id"}
  }'
```

### List services
```bash
aws apprunner list-services \
  --query 'ServiceSummaryList[].{Name:ServiceName,Status:Status,Url:ServiceUrl}'
```

### Deploy a new version
```bash
aws apprunner start-deployment \
  --service-arn arn:aws:apprunner:us-east-1:123456789012:service/my-api/id
```

### Associate a custom domain
```bash
aws apprunner associate-custom-domain \
  --service-arn arn:aws:apprunner:us-east-1:123456789012:service/my-api/id \
  --domain-name api.example.com
```

### Pause a service
```bash
aws apprunner pause-service \
  --service-arn arn:aws:apprunner:us-east-1:123456789012:service/my-api/id
```

### Resume a paused service
```bash
aws apprunner resume-service \
  --service-arn arn:aws:apprunner:us-east-1:123456789012:service/my-api/id
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Services | [`services.md`](services.md) | create-service, describe-service, list-services, update-service, delete-service, pause-service, resume-service, start-deployment, list-operations |
| Connections | [`connections.md`](connections.md) | create-connection, describe-connection, list-connections, delete-connection |
| Auto Scaling | [`auto-scaling.md`](auto-scaling.md) | create-auto-scaling-configuration, delete-auto-scaling-configuration, describe-auto-scaling-configuration, list-auto-scaling-configurations, list-services-for-auto-scaling-configuration, update-default-auto-scaling-configuration |
| Observability | [`observability.md`](observability.md) | create-observability-configuration, delete-observability-configuration, describe-observability-configuration, list-observability-configurations |
| VPC | [`vpc.md`](vpc.md) | create-vpc-connector, delete-vpc-connector, describe-vpc-connector, list-vpc-connectors, create-vpc-ingress-connection, delete-vpc-ingress-connection, describe-vpc-ingress-connection, list-vpc-ingress-connections, update-vpc-ingress-connection |
| Custom Domains | [`custom-domains.md`](custom-domains.md) | associate-custom-domain, disassociate-custom-domain, describe-custom-domains |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
