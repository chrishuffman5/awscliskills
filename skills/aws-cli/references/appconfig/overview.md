# AWS CLI v2 — AppConfig

## Overview

Complete reference for all `aws appconfig` and `aws appconfigdata` subcommands in AWS CLI v2. Covers application management, configuration profiles, environments, deployment strategies, deployments, hosted configuration versions, extensions, extension associations, configuration validation, account settings, and real-time configuration data retrieval. AppConfig is a feature of AWS Systems Manager that enables controlled deployments of configuration data to applications at runtime, with built-in validation, monitoring, and automatic rollback.

## Quick Reference — Common Workflows

### Create an application with environment and configuration profile
```bash
aws appconfig create-application \
    --name my-app \
    --description "Production application"

aws appconfig create-environment \
    --application-id abc1234 \
    --name Production \
    --monitors '[{"AlarmArn":"arn:aws:cloudwatch:us-east-1:123456789012:alarm:MyAlarm"}]'

aws appconfig create-configuration-profile \
    --application-id abc1234 \
    --name my-config \
    --location-uri hosted \
    --type AWS.Freeform
```

### Create and deploy a hosted configuration
```bash
aws appconfig create-hosted-configuration-version \
    --application-id abc1234 \
    --configuration-profile-id ur8hx2f \
    --content '{"feature_enabled":true,"max_items":100}' \
    --content-type application/json \
    output.json

aws appconfig create-deployment-strategy \
    --name Linear50Percent \
    --deployment-duration-in-minutes 10 \
    --growth-factor 50 \
    --growth-type LINEAR \
    --replicate-to NONE

aws appconfig start-deployment \
    --application-id abc1234 \
    --environment-id 54j1r29 \
    --deployment-strategy-id 1225qzk \
    --configuration-profile-id ur8hx2f \
    --configuration-version 1
```

### Retrieve configuration at runtime (appconfigdata)
```bash
TOKEN=$(aws appconfigdata start-configuration-session \
    --application-identifier my-app \
    --environment-identifier Production \
    --configuration-profile-identifier my-config \
    --query 'InitialConfigurationToken' --output text)

aws appconfigdata get-latest-configuration \
    --configuration-token "$TOKEN" \
    config_output.json
```

### Create an extension with Lambda action
```bash
aws appconfig create-extension \
    --name my-validator \
    --actions 'PRE_START_DEPLOYMENT=[{Name=Validate,Uri=arn:aws:lambda:us-east-1:123456789012:function:validate-config,RoleArn=arn:aws:iam::123456789012:role/AppConfigExtensionRole}]'

aws appconfig create-extension-association \
    --extension-identifier my-validator \
    --resource-identifier "arn:aws:appconfig:us-east-1:123456789012:application/abc1234"
```

### Feature flags workflow
```bash
aws appconfig create-configuration-profile \
    --application-id abc1234 \
    --name feature-flags \
    --location-uri hosted \
    --type AWS.AppConfig.FeatureFlags

aws appconfig create-hosted-configuration-version \
    --application-id abc1234 \
    --configuration-profile-id ff1234 \
    --content '{"version":"1","flags":{"new_dashboard":{"name":"new_dashboard"}},"values":{"new_dashboard":{"enabled":true}}}' \
    --content-type application/json \
    flags_output.json
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Applications | [applications.md](applications.md) | `create-application`, `get-application`, `list-applications`, `update-application`, `delete-application` |
| Configuration Profiles | [configuration-profiles.md](configuration-profiles.md) | `create-configuration-profile`, `get-configuration-profile`, `list-configuration-profiles`, `update-configuration-profile`, `delete-configuration-profile` |
| Environments | [environments.md](environments.md) | `create-environment`, `get-environment`, `list-environments`, `update-environment`, `delete-environment` |
| Deployment Strategies | [deployment-strategies.md](deployment-strategies.md) | `create-deployment-strategy`, `get-deployment-strategy`, `list-deployment-strategies`, `update-deployment-strategy`, `delete-deployment-strategy` |
| Deployments | [deployments.md](deployments.md) | `start-deployment`, `get-deployment`, `list-deployments`, `stop-deployment` |
| Hosted Configuration Versions | [hosted-configuration-versions.md](hosted-configuration-versions.md) | `create-hosted-configuration-version`, `get-hosted-configuration-version`, `list-hosted-configuration-versions`, `delete-hosted-configuration-version` |
| Extensions | [extensions.md](extensions.md) | `create-extension`, `get-extension`, `list-extensions`, `update-extension`, `delete-extension`, `create-extension-association`, `get-extension-association`, `list-extension-associations`, `update-extension-association`, `delete-extension-association` |
| Validation & Settings | [validation-settings.md](validation-settings.md) | `validate-configuration`, `get-account-settings`, `update-account-settings` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
| AppConfigData | [appconfigdata.md](appconfigdata.md) | `start-configuration-session`, `get-latest-configuration` |
