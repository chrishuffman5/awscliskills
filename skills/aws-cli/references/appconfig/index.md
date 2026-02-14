# AppConfig — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-application` | Create an application namespace |
| `get-application` | Retrieve application details |
| `list-applications` | List all applications |
| `update-application` | Modify an application |
| `delete-application` | Delete an application |
| `create-configuration-profile` | Create a configuration profile |
| `get-configuration-profile` | Retrieve configuration profile details |
| `list-configuration-profiles` | List configuration profiles for an application |
| `update-configuration-profile` | Modify a configuration profile |
| `delete-configuration-profile` | Delete a configuration profile |
| `create-environment` | Create an environment for an application |
| `get-environment` | Retrieve environment details |
| `list-environments` | List environments for an application |
| `update-environment` | Modify an environment |
| `delete-environment` | Delete an environment |
| `create-deployment-strategy` | Create a deployment strategy |
| `get-deployment-strategy` | Retrieve deployment strategy details |
| `list-deployment-strategies` | List all deployment strategies |
| `update-deployment-strategy` | Modify a deployment strategy |
| `delete-deployment-strategy` | Delete a deployment strategy |
| `start-deployment` | Start a configuration deployment |
| `get-deployment` | Retrieve deployment details |
| `list-deployments` | List deployments for an environment |
| `stop-deployment` | Stop an ongoing deployment |
| `create-hosted-configuration-version` | Create a hosted configuration version |
| `get-hosted-configuration-version` | Retrieve a hosted configuration version |
| `list-hosted-configuration-versions` | List hosted configuration versions |
| `delete-hosted-configuration-version` | Delete a hosted configuration version |
| `create-extension` | Create an extension |
| `get-extension` | Retrieve extension details |
| `list-extensions` | List all extensions |
| `update-extension` | Modify an extension |
| `delete-extension` | Delete an extension |
| `create-extension-association` | Associate an extension with a resource |
| `get-extension-association` | Retrieve extension association details |
| `list-extension-associations` | List extension associations |
| `update-extension-association` | Modify an extension association |
| `delete-extension-association` | Delete an extension association |
| `validate-configuration` | Validate configuration data |
| `get-account-settings` | Retrieve account-level settings |
| `update-account-settings` | Modify account-level settings |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |

### AppConfigData Commands

| Command | Description |
|---------|-------------|
| `start-configuration-session` | Start a configuration session for retrieving data |
| `get-latest-configuration` | Retrieve the latest configuration data |

## Global Options

All commands accept these options:

| Option | Description |
|--------|-------------|
| `--output` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | JMESPath query to filter output |
| `--region` | AWS region |
| `--profile` | Named credential profile |
| `--no-cli-pager` | Disable pager for output |
| `--cli-input-json` | Read parameters from JSON string |
| `--cli-input-yaml` | Read parameters from YAML string |
| `--generate-cli-skeleton` | Print JSON/YAML input skeleton |

## Common Patterns

### Check deployment status
```bash
aws appconfig get-deployment \
    --application-id abc1234 \
    --environment-id 54j1r29 \
    --deployment-number 1 \
    --query '{State:State,Percentage:PercentageComplete,Version:ConfigurationVersion}'
```

### List all feature flag profiles
```bash
aws appconfig list-configuration-profiles \
    --application-id abc1234 \
    --type AWS.AppConfig.FeatureFlags \
    --query 'Items[].{Id:Id,Name:Name}'
```

### Get latest hosted configuration version number
```bash
aws appconfig list-hosted-configuration-versions \
    --application-id abc1234 \
    --configuration-profile-id ur8hx2f \
    --max-results 1 \
    --query 'Items[0].VersionNumber'
```
