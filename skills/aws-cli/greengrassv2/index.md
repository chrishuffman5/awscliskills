# IoT Greengrass v2 — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `associate-service-role-to-account` | Associate a service role with your account |
| `batch-associate-client-device-with-core-device` | Associate client devices with a core device |
| `batch-disassociate-client-device-from-core-device` | Disassociate client devices from a core device |
| `cancel-deployment` | Cancel a deployment |
| `create-component-version` | Create a new component version from recipe or Lambda |
| `create-deployment` | Create a deployment to a core device or thing group |
| `delete-component` | Delete a component version |
| `delete-core-device` | Delete a core device |
| `delete-deployment` | Delete a deployment |
| `describe-component` | Get metadata about a component version |
| `disassociate-service-role-from-account` | Remove the service role from your account |
| `get-component` | Get the recipe for a component version |
| `get-component-version-artifact` | Get a presigned URL for a component artifact |
| `get-connectivity-info` | Get connectivity info for a core device |
| `get-core-device` | Get details about a core device |
| `get-deployment` | Get details about a deployment |
| `get-service-role-for-account` | Get the service role for your account |
| `list-client-devices-associated-with-core-device` | List client devices associated with a core device |
| `list-component-versions` | List versions of a component |
| `list-components` | List components |
| `list-core-devices` | List core devices |
| `list-deployments` | List deployments |
| `list-effective-deployments` | List deployments that apply to a core device |
| `list-installed-components` | List components installed on a core device |
| `list-tags-for-resource` | List tags for a resource |
| `resolve-component-candidates` | Identify components that meet requirements |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `update-connectivity-info` | Update connectivity info for a core device |

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

### List healthy core devices
```bash
aws greengrassv2 list-core-devices --status HEALTHY \
    --query 'coreDevices[].{Name:coreDeviceThingName,Version:coreVersion,Updated:lastStatusUpdateTimestamp}'
```

### Check deployment status for a device
```bash
aws greengrassv2 list-effective-deployments \
    --core-device-thing-name MyGreengrassCore \
    --query 'effectiveDeployments[].{Name:deploymentName,Status:coreDeviceExecutionStatus,Modified:modifiedTimestamp}'
```

### List running components on a device
```bash
aws greengrassv2 list-installed-components \
    --core-device-thing-name MyGreengrassCore \
    --topology-filter ALL \
    --query 'installedComponents[?lifecycleState==`RUNNING`].{Name:componentName,Version:componentVersion}'
```
