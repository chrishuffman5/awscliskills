# AWS CLI v2 -- Snow Family (Snowball) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/snowball/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-job` | Job | Create a Snow Family import, export, or local use job |
| `describe-job` | Job | Get details about a specific job |
| `update-job` | Job | Update a job's configuration (while in New state) |
| `cancel-job` | Job | Cancel a job before device preparation begins |
| `list-jobs` | Job | List all Snow Family jobs in the account |
| `get-job-manifest` | Job | Get the presigned URL for the job manifest file |
| `get-job-unlock-code` | Job | Get the unlock code for a Snow device |
| `get-software-updates` | Job | Get presigned URL for software updates |
| `update-job-shipment-state` | Job | Update the shipment state of a job |
| `create-cluster` | Cluster | Create a cluster of Snow devices |
| `describe-cluster` | Cluster | Get details about a specific cluster |
| `update-cluster` | Cluster | Update a cluster configuration (while in AwaitingQuorum state) |
| `cancel-cluster` | Cluster | Cancel a cluster job |
| `list-clusters` | Cluster | List all clusters in the account |
| `list-cluster-jobs` | Cluster | List jobs associated with a cluster |
| `create-address` | Address | Create a shipping address for Snow devices |
| `describe-address` | Address | Get details about a specific address |
| `describe-addresses` | Address | List and describe all addresses |
| `list-pickup-locations` | Address | List available device pickup locations |
| `create-long-term-pricing` | Pricing | Create a long-term pricing agreement |
| `update-long-term-pricing` | Pricing | Update a long-term pricing agreement |
| `list-long-term-pricing` | Pricing | List all long-term pricing agreements |
| `create-return-shipping-label` | Shipping | Create a return shipping label for a job |
| `describe-return-shipping-label` | Shipping | Get details about a return shipping label |
| `get-snowball-usage` | Compatibility | Get account usage limits and current usage |
| `list-compatible-images` | Compatibility | List compatible AMIs for Snow devices |
| `list-service-versions` | Compatibility | List supported service versions for Snow devices |

---

## Global Options

These options are available on ALL `aws snowball` commands.

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

### Job ID Format
- **Length:** 39 characters
- **Pattern:** `(M|J)ID[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12}`
- Example: `JID123e4567-e89b-12d3-a456-426655440000`

### Cluster ID Format
- **Length:** 39 characters
- **Pattern:** `CID[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12}`

### Address ID Format
- **Length:** 40 characters
- **Pattern:** `ADID[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12}`

### Job States
| State | Description |
|-------|-------------|
| `New` | Job has been created |
| `PreparingAppliance` | Device is being prepared |
| `PreparingShipment` | Shipment is being prepared |
| `InTransitToCustomer` | Device is in transit to customer |
| `WithCustomer` | Device is with the customer |
| `InTransitToAWS` | Device is in transit back to AWS |
| `WithAWSSortingFacility` | Device is at AWS sorting facility |
| `WithAWS` | Device is with AWS |
| `InProgress` | Data transfer in progress |
| `Complete` | Job is complete |
| `Cancelled` | Job has been cancelled |
| `Listing` | Listing export jobs |
| `Pending` | Job is pending |

### Cluster States
| State | Description |
|-------|-------------|
| `AwaitingQuorum` | Waiting for all node jobs to be created |
| `Pending` | Cluster is pending |
| `InUse` | Cluster is in use |
| `Complete` | Cluster is complete |
| `Cancelled` | Cluster has been cancelled |

### Snow Device Types
| Type | Description |
|------|-------------|
| `STANDARD` | Standard Snowball (legacy) |
| `EDGE` | Snowball Edge Storage Optimized |
| `EDGE_C` | Snowball Edge Compute Optimized |
| `EDGE_CG` | Snowball Edge Compute Optimized with GPU |
| `EDGE_S` | Snowball Edge Storage Optimized (with EC2) |
| `SNC1_HDD` | Snowcone HDD |
| `SNC1_SSD` | Snowcone SSD |
| `V3_5C` | Snowball Edge V3.5 Compute |
| `V3_5S` | Snowball Edge V3.5 Storage |
| `RACK_5U_C` | Snow device rack mount |
