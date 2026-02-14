# MediaConnect — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-flow` | Create a new flow |
| `describe-flow` | Describe a flow |
| `list-flows` | List all flows |
| `update-flow` | Update a flow |
| `delete-flow` | Delete a flow |
| `start-flow` | Start a flow |
| `stop-flow` | Stop a flow |
| `describe-flow-source-metadata` | Describe flow source metadata |
| `describe-flow-source-thumbnail` | Describe flow source thumbnail |
| `add-flow-sources` | Add sources to a flow |
| `update-flow-source` | Update a flow source |
| `remove-flow-source` | Remove a flow source |
| `add-flow-outputs` | Add outputs to a flow |
| `update-flow-output` | Update a flow output |
| `remove-flow-output` | Remove a flow output |
| `grant-flow-entitlements` | Grant entitlements on a flow |
| `update-flow-entitlement` | Update a flow entitlement |
| `revoke-flow-entitlement` | Revoke a flow entitlement |
| `list-entitlements` | List all entitlements |
| `add-flow-media-streams` | Add media streams to a flow |
| `update-flow-media-stream` | Update a flow media stream |
| `remove-flow-media-stream` | Remove a flow media stream |
| `add-flow-vpc-interfaces` | Add VPC interfaces to a flow |
| `remove-flow-vpc-interface` | Remove a VPC interface from a flow |
| `create-bridge` | Create a bridge |
| `describe-bridge` | Describe a bridge |
| `list-bridges` | List all bridges |
| `update-bridge` | Update a bridge |
| `update-bridge-state` | Update bridge state (start/stop) |
| `delete-bridge` | Delete a bridge |
| `add-bridge-sources` | Add sources to a bridge |
| `update-bridge-source` | Update a bridge source |
| `remove-bridge-source` | Remove a bridge source |
| `add-bridge-outputs` | Add outputs to a bridge |
| `update-bridge-output` | Update a bridge output |
| `remove-bridge-output` | Remove a bridge output |
| `create-gateway` | Create a gateway |
| `describe-gateway` | Describe a gateway |
| `list-gateways` | List all gateways |
| `delete-gateway` | Delete a gateway |
| `describe-gateway-instance` | Describe a gateway instance |
| `list-gateway-instances` | List gateway instances |
| `update-gateway-instance` | Update a gateway instance |
| `deregister-gateway-instance` | Deregister a gateway instance |
| `create-router-input` | Create a router input |
| `get-router-input` | Get router input details |
| `list-router-inputs` | List router inputs |
| `update-router-input` | Update a router input |
| `delete-router-input` | Delete a router input |
| `start-router-input` | Start a router input |
| `stop-router-input` | Stop a router input |
| `restart-router-input` | Restart a router input |
| `take-router-input` | Take a router input |
| `batch-get-router-input` | Batch get router inputs |
| `get-router-input-source-metadata` | Get router input source metadata |
| `get-router-input-thumbnail` | Get router input thumbnail |
| `create-router-output` | Create a router output |
| `get-router-output` | Get router output details |
| `list-router-outputs` | List router outputs |
| `update-router-output` | Update a router output |
| `delete-router-output` | Delete a router output |
| `start-router-output` | Start a router output |
| `stop-router-output` | Stop a router output |
| `restart-router-output` | Restart a router output |
| `batch-get-router-output` | Batch get router outputs |
| `create-router-network-interface` | Create a router network interface |
| `get-router-network-interface` | Get router network interface |
| `list-router-network-interfaces` | List router network interfaces |
| `update-router-network-interface` | Update a router network interface |
| `delete-router-network-interface` | Delete a router network interface |
| `batch-get-router-network-interface` | Batch get router network interfaces |
| `list-offerings` | List available reservation offerings |
| `describe-offering` | Describe a reservation offering |
| `purchase-offering` | Purchase a reservation |
| `list-reservations` | List reservations |
| `describe-reservation` | Describe a reservation |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |
| `tag-global-resource` | Add tags to a global resource |
| `untag-global-resource` | Remove tags from a global resource |
| `list-tags-for-global-resource` | List tags for a global resource |

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

### List all active flows
```bash
aws mediaconnect list-flows \
    --query 'Flows[?Status==`ACTIVE`].{Name:Name,ARN:FlowArn,AZ:AvailabilityZone}'
```

### Get ingest endpoint for a flow
```bash
aws mediaconnect describe-flow \
    --flow-arn arn:aws:mediaconnect:us-east-1:123456789012:flow:1-abc:MyFlow \
    --query 'Flow.Source.{IP:IngestIp,Port:IngestPort,Protocol:Transport.Protocol}'
```

### List all output destinations for a flow
```bash
aws mediaconnect describe-flow \
    --flow-arn arn:aws:mediaconnect:us-east-1:123456789012:flow:1-abc:MyFlow \
    --query 'Flow.Outputs[].{Name:Name,Dest:Destination,Port:Port,Status:OutputStatus}'
```
