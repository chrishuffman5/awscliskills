# Amazon MQ — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-broker` | Create a message broker |
| `describe-broker` | Get detailed broker information |
| `list-brokers` | List all message brokers |
| `update-broker` | Update broker settings |
| `delete-broker` | Delete a message broker |
| `reboot-broker` | Reboot a message broker |
| `promote` | Promote a data replication replica broker to primary |
| `describe-broker-engine-types` | List available broker engine types and versions |
| `describe-broker-instance-options` | List available broker instance options |
| `create-configuration` | Create a broker configuration |
| `describe-configuration` | Get configuration details |
| `list-configurations` | List all configurations |
| `update-configuration` | Update a configuration with new data |
| `delete-configuration` | Delete a broker configuration |
| `describe-configuration-revision` | Get a specific configuration revision |
| `list-configuration-revisions` | List configuration revisions |
| `create-user` | Create a broker user |
| `describe-user` | Get user details |
| `list-users` | List all users for a broker |
| `update-user` | Update user settings |
| `delete-user` | Delete a broker user |
| `create-tags` | Add tags to a resource |
| `list-tags` | List tags for a resource |
| `delete-tags` | Remove tags from a resource |

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

### List all brokers with their state
```bash
aws mq list-brokers \
    --query 'BrokerSummaries[].{Name:BrokerName,Id:BrokerId,State:BrokerState,Engine:EngineType,Mode:DeploymentMode}'
```

### Get broker connection endpoints
```bash
aws mq describe-broker --broker-id b-abc123 \
    --query 'BrokerInstances[].{Console:ConsoleURL,Endpoints:Endpoints}'
```

### Check for required actions on a broker
```bash
aws mq describe-broker --broker-id b-abc123 \
    --query 'ActionsRequired[].{Code:ActionRequiredCode,Info:ActionRequiredInfo}'
```
