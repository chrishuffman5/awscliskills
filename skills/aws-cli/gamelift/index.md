# AWS CLI v2 -- GameLift Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/gamelift/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `accept-match` | Matchmaking | Accept or reject a proposed FlexMatch match |
| `claim-game-server` | Game Server Group | Locate and reserve a game server in a game server group |
| `create-alias` | Alias | Create an alias for a fleet |
| `create-build` | Build | Create a new custom game server build |
| `create-container-fleet` | Container Fleet | Create a new container-based fleet |
| `create-container-group-definition` | Container Fleet | Create a container group definition |
| `create-fleet` | Fleet | Create a new EC2 or Anywhere fleet |
| `create-fleet-locations` | Fleet | Add remote locations to a multi-location fleet |
| `create-game-server-group` | Game Server Group | Create a FleetIQ game server group |
| `create-game-session` | Game Session | Create a new game session on a fleet |
| `create-game-session-queue` | Game Session | Create a game session placement queue |
| `create-location` | Location | Create a custom location for Anywhere fleets |
| `create-matchmaking-configuration` | Matchmaking | Create a FlexMatch matchmaking configuration |
| `create-matchmaking-rule-set` | Matchmaking | Create a FlexMatch matchmaking rule set |
| `create-player-session` | Player Session | Reserve a player slot in a game session |
| `create-player-sessions` | Player Session | Reserve multiple player slots in a game session |
| `create-script` | Script | Create a Realtime Servers script |
| `create-vpc-peering-authorization` | VPC Peering | Authorize VPC peering with a GameLift fleet |
| `create-vpc-peering-connection` | VPC Peering | Establish a VPC peering connection |
| `delete-alias` | Alias | Delete a fleet alias |
| `delete-build` | Build | Delete a game server build |
| `delete-container-fleet` | Container Fleet | Delete a container fleet |
| `delete-container-group-definition` | Container Fleet | Delete a container group definition |
| `delete-fleet` | Fleet | Delete a fleet |
| `delete-fleet-locations` | Fleet | Remove remote locations from a fleet |
| `delete-game-server-group` | Game Server Group | Delete a FleetIQ game server group |
| `delete-game-session-queue` | Game Session | Delete a game session queue |
| `delete-location` | Location | Delete a custom location |
| `delete-matchmaking-configuration` | Matchmaking | Delete a matchmaking configuration |
| `delete-matchmaking-rule-set` | Matchmaking | Delete a matchmaking rule set |
| `delete-scaling-policy` | Scaling | Delete a fleet scaling policy |
| `delete-script` | Script | Delete a Realtime Servers script |
| `delete-vpc-peering-authorization` | VPC Peering | Delete a VPC peering authorization |
| `delete-vpc-peering-connection` | VPC Peering | Delete a VPC peering connection |
| `deregister-compute` | Compute | Remove a registered compute from a fleet |
| `deregister-game-server` | Game Server Group | Remove a game server from a game server group |
| `describe-alias` | Alias | Retrieve properties of a fleet alias |
| `describe-build` | Build | Retrieve properties of a game build |
| `describe-compute` | Compute | Retrieve properties of a registered compute |
| `describe-container-fleet` | Container Fleet | Retrieve properties of a container fleet |
| `describe-container-group-definition` | Container Fleet | Retrieve a container group definition |
| `describe-ec2-instance-limits` | Fleet | Retrieve EC2 instance limits for GameLift |
| `describe-fleet-attributes` | Fleet | Retrieve fleet properties |
| `describe-fleet-capacity` | Fleet | Retrieve fleet capacity settings |
| `describe-fleet-deployment` | Fleet | Retrieve details of a fleet deployment |
| `describe-fleet-events` | Fleet | Retrieve fleet event log entries |
| `describe-fleet-location-attributes` | Fleet | Retrieve location properties for a fleet |
| `describe-fleet-location-capacity` | Fleet | Retrieve capacity for a fleet location |
| `describe-fleet-location-utilization` | Fleet | Retrieve utilization for a fleet location |
| `describe-fleet-port-settings` | Fleet | Retrieve inbound connection permissions for a fleet |
| `describe-fleet-utilization` | Fleet | Retrieve fleet utilization statistics |
| `describe-game-server` | Game Server Group | Retrieve properties of a registered game server |
| `describe-game-server-group` | Game Server Group | Retrieve a game server group |
| `describe-game-server-instances` | Game Server Group | Track instances in a game server group |
| `describe-game-session-details` | Game Session | Retrieve game sessions with protection policy |
| `describe-game-session-placement` | Game Session | Retrieve a game session placement request |
| `describe-game-session-queues` | Game Session | Retrieve game session queue properties |
| `describe-game-sessions` | Game Session | Retrieve active game sessions |
| `describe-instances` | Fleet | Retrieve information about fleet instances |
| `describe-matchmaking` | Matchmaking | Retrieve matchmaking ticket details |
| `describe-matchmaking-configurations` | Matchmaking | Retrieve matchmaking configurations |
| `describe-matchmaking-rule-sets` | Matchmaking | Retrieve matchmaking rule sets |
| `describe-player-sessions` | Player Session | Retrieve player session properties |
| `describe-runtime-configuration` | Fleet | Retrieve runtime configuration for a fleet |
| `describe-scaling-policies` | Scaling | Retrieve fleet scaling policies |
| `describe-script` | Script | Retrieve properties of a Realtime script |
| `describe-vpc-peering-authorizations` | VPC Peering | Retrieve VPC peering authorizations |
| `describe-vpc-peering-connections` | VPC Peering | Retrieve VPC peering connections |
| `get-compute-access` | Compute | Get credentials to remotely access a compute |
| `get-compute-auth-token` | Compute | Get an authentication token for a compute |
| `get-game-session-log` | Game Session | Download game session logs (deprecated) |
| `get-game-session-log-url` | Game Session | Get a presigned URL for game session logs |
| `get-instance-access` | Fleet | Get remote access credentials for a fleet instance |
| `list-aliases` | Alias | List all aliases in the account |
| `list-builds` | Build | List all builds in the account |
| `list-compute` | Compute | List compute resources in a fleet |
| `list-container-fleets` | Container Fleet | List container fleets |
| `list-container-group-definition-versions` | Container Fleet | List versions of a container group definition |
| `list-container-group-definitions` | Container Fleet | List container group definitions |
| `list-fleet-deployments` | Fleet | List deployments for a fleet |
| `list-fleets` | Fleet | List all fleets in the account |
| `list-game-server-groups` | Game Server Group | List FleetIQ game server groups |
| `list-game-servers` | Game Server Group | List game servers in a group |
| `list-locations` | Location | List custom locations |
| `list-scripts` | Script | List all Realtime scripts |
| `list-tags-for-resource` | Tags | List tags for a GameLift resource |
| `put-scaling-policy` | Scaling | Create or update a fleet scaling policy |
| `register-compute` | Compute | Register a compute resource to a fleet |
| `register-game-server` | Game Server Group | Register a game server in a group |
| `request-upload-credentials` | Build | Get fresh upload credentials for a build |
| `resolve-alias` | Alias | Retrieve the fleet ID an alias points to |
| `resume-game-server-group` | Game Server Group | Resume auto-scaling activity |
| `search-game-sessions` | Game Session | Search for active game sessions |
| `start-fleet-actions` | Scaling | Resume auto-scaling for a fleet |
| `start-game-session-placement` | Game Session | Place a game session request in a queue |
| `start-match-backfill` | Matchmaking | Backfill an existing game session with new players |
| `start-matchmaking` | Matchmaking | Start a matchmaking request |
| `stop-fleet-actions` | Scaling | Suspend auto-scaling for a fleet |
| `stop-game-session-placement` | Game Session | Cancel a game session placement request |
| `stop-matchmaking` | Matchmaking | Cancel a matchmaking request |
| `suspend-game-server-group` | Game Server Group | Suspend auto-scaling activity |
| `tag-resource` | Tags | Add tags to a GameLift resource |
| `terminate-game-session` | Game Session | Terminate an active game session |
| `untag-resource` | Tags | Remove tags from a GameLift resource |
| `update-alias` | Alias | Update alias properties |
| `update-build` | Build | Update build metadata |
| `update-container-fleet` | Container Fleet | Update container fleet properties |
| `update-container-group-definition` | Container Fleet | Update a container group definition |
| `update-fleet-attributes` | Fleet | Update fleet attributes |
| `update-fleet-capacity` | Fleet | Update fleet capacity settings |
| `update-fleet-port-settings` | Fleet | Update fleet port settings |
| `update-game-server` | Game Server Group | Update game server properties |
| `update-game-server-group` | Game Server Group | Update game server group properties |
| `update-game-session` | Game Session | Update game session properties |
| `update-game-session-queue` | Game Session | Update game session queue properties |
| `update-matchmaking-configuration` | Matchmaking | Update matchmaking configuration |
| `update-runtime-configuration` | Fleet | Update fleet runtime configuration |
| `update-script` | Script | Update Realtime script properties |
| `upload-build` | Build | Upload a game server build from local files |
| `validate-matchmaking-rule-set` | Matchmaking | Validate a matchmaking rule set |

---

## Global Options

These options are available on ALL `aws gamelift` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Fleet Status Values
| Status | Description |
|--------|-------------|
| `NEW` | Fleet has been created |
| `DOWNLOADING` | Build/script is downloading to instances |
| `VALIDATING` | Build/script is being validated |
| `BUILDING` | Build is being installed |
| `ACTIVATING` | Fleet is starting server processes |
| `ACTIVE` | Fleet is ready for game sessions |
| `DELETING` | Fleet is being deleted |
| `ERROR` | Fleet encountered an error |
| `TERMINATED` | Fleet has been terminated |
| `NOT_FOUND` | Fleet was not found |

### Game Session Status Values
| Status | Description |
|--------|-------------|
| `ACTIVE` | Game session is accepting players |
| `ACTIVATING` | Game session is starting up |
| `TERMINATED` | Game session has ended |
| `TERMINATING` | Game session is shutting down |
| `ERROR` | Game session encountered an error |

### Build Status Values
| Status | Description |
|--------|-------------|
| `INITIALIZED` | Build created but files not yet uploaded |
| `READY` | Build files uploaded and validated |
| `FAILED` | Build validation failed |

### Matchmaking Ticket Status Values
| Status | Description |
|--------|-------------|
| `QUEUED` | Ticket is waiting for processing |
| `SEARCHING` | Actively searching for matches |
| `REQUIRES_ACCEPTANCE` | Match found, waiting for acceptance |
| `PLACING` | Match accepted, placing game session |
| `COMPLETED` | Match placed successfully |
| `CANCELLED` | Ticket was cancelled |
| `TIMED_OUT` | Ticket timed out |
| `FAILED` | Matchmaking failed |
