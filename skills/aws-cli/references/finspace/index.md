# AWS CLI v2 -- FinSpace Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/finspace/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-environment` | Environment | Create a legacy FinSpace environment |
| `delete-environment` | Environment | Delete a legacy FinSpace environment |
| `get-environment` | Environment | Get details of a legacy environment |
| `list-environments` | Environment | List all legacy environments |
| `update-environment` | Environment | Update a legacy environment |
| `create-kx-environment` | KX Environment | Create a KX (kdb+) environment |
| `delete-kx-environment` | KX Environment | Delete a KX environment |
| `get-kx-environment` | KX Environment | Get details of a KX environment |
| `list-kx-environments` | KX Environment | List all KX environments |
| `update-kx-environment` | KX Environment | Update a KX environment |
| `update-kx-environment-network` | KX Environment | Update KX environment network configuration |
| `create-kx-database` | Database | Create a KX database |
| `delete-kx-database` | Database | Delete a KX database |
| `get-kx-database` | Database | Get details of a KX database |
| `list-kx-databases` | Database | List KX databases |
| `update-kx-database` | Database | Update a KX database |
| `create-kx-cluster` | Cluster | Create a KX cluster |
| `delete-kx-cluster` | Cluster | Delete a KX cluster |
| `get-kx-cluster` | Cluster | Get details of a KX cluster |
| `list-kx-clusters` | Cluster | List KX clusters |
| `update-kx-cluster-code-configuration` | Cluster | Update cluster code configuration |
| `update-kx-cluster-databases` | Cluster | Update cluster database caches |
| `delete-kx-cluster-node` | Cluster | Delete a specific cluster node |
| `list-kx-cluster-nodes` | Cluster | List nodes in a cluster |
| `get-kx-connection-string` | Cluster | Get a connection string for a cluster |
| `create-kx-dataview` | Dataview | Create a KX dataview |
| `delete-kx-dataview` | Dataview | Delete a KX dataview |
| `get-kx-dataview` | Dataview | Get details of a KX dataview |
| `list-kx-dataviews` | Dataview | List KX dataviews |
| `update-kx-dataview` | Dataview | Update a KX dataview |
| `create-kx-changeset` | Changeset | Create a changeset to load data |
| `get-kx-changeset` | Changeset | Get details of a changeset |
| `list-kx-changesets` | Changeset | List changesets for a database |
| `create-kx-scaling-group` | Scaling Group | Create a KX scaling group |
| `delete-kx-scaling-group` | Scaling Group | Delete a KX scaling group |
| `get-kx-scaling-group` | Scaling Group | Get details of a scaling group |
| `list-kx-scaling-groups` | Scaling Group | List scaling groups |
| `create-kx-volume` | Volume | Create a KX volume |
| `delete-kx-volume` | Volume | Delete a KX volume |
| `get-kx-volume` | Volume | Get details of a KX volume |
| `list-kx-volumes` | Volume | List KX volumes |
| `update-kx-volume` | Volume | Update a KX volume |
| `create-kx-user` | User | Create a KX user |
| `delete-kx-user` | User | Delete a KX user |
| `get-kx-user` | User | Get details of a KX user |
| `list-kx-users` | User | List KX users |
| `update-kx-user` | User | Update a KX user |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws finspace` commands.

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

### KX Cluster Types

| Type | Description |
|------|-------------|
| `HDB` | Historical Database — serves queries on historical data |
| `RDB` | Realtime Database — captures and serves streaming data |
| `GATEWAY` | Gateway — routes queries to HDB and RDB clusters |
| `GP` | General Purpose — runs custom kdb+ code |
| `TICKERPLANT` | Tickerplant — captures and distributes streaming data |

### KX Cluster Statuses

| Status | Description |
|--------|-------------|
| `PENDING` | Cluster creation is pending |
| `CREATING` | Cluster is being created |
| `CREATE_FAILED` | Cluster creation failed |
| `RUNNING` | Cluster is operational |
| `UPDATING` | Cluster is being updated |
| `DELETING` | Cluster is being deleted |
| `DELETED` | Cluster has been deleted |
| `DELETE_FAILED` | Cluster deletion failed |

### KX Environment Statuses

| Status | Description |
|--------|-------------|
| `CREATE_REQUESTED` | Environment creation requested |
| `CREATING` | Environment is being created |
| `CREATED` | Environment is ready |
| `DELETE_REQUESTED` | Deletion requested |
| `DELETING` | Environment is being deleted |
| `DELETED` | Environment has been deleted |
| `FAILED_CREATION` | Environment creation failed |
| `RETRY_DELETION` | Retrying deletion |
| `FAILED_DELETION` | Deletion failed |
| `UPDATE_NETWORK_REQUESTED` | Network update requested |
| `UPDATING_NETWORK` | Network is being updated |
| `FAILED_UPDATING_NETWORK` | Network update failed |
| `SUSPENDED` | Environment is suspended |

### Changeset Statuses

| Status | Description |
|--------|-------------|
| `PENDING` | Changeset is pending processing |
| `PROCESSING` | Changeset is being processed |
| `FAILED` | Changeset processing failed |
| `COMPLETED` | Changeset processed successfully |

### AZ Modes

| Mode | Description |
|------|-------------|
| `SINGLE` | Single Availability Zone |
| `MULTI` | Multiple Availability Zones |
