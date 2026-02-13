# AWS CLI v2 -- Lightsail Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/lightsail/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-instances` | Instance | Create one or more Lightsail instances |
| `create-instances-from-snapshot` | Instance | Create instances from a snapshot |
| `delete-instance` | Instance | Delete a Lightsail instance |
| `get-instance` | Instance | Get details for a specific instance |
| `get-instances` | Instance | Get details for all instances |
| `get-instance-state` | Instance | Get the state of an instance |
| `get-instance-access-details` | Instance | Get SSH/RDP access details for an instance |
| `get-instance-metric-data` | Instance | Get instance metric data |
| `get-instance-port-states` | Instance | Get firewall port states for an instance |
| `reboot-instance` | Instance | Reboot an instance |
| `start-instance` | Instance | Start a stopped instance |
| `stop-instance` | Instance | Stop a running instance |
| `update-instance-metadata-options` | Instance | Update instance metadata options |
| `open-instance-public-ports` | Instance | Open firewall ports on an instance |
| `close-instance-public-ports` | Instance | Close firewall ports on an instance |
| `put-instance-public-ports` | Instance | Replace all firewall port rules on an instance |
| `set-ip-address-type` | Instance | Set the IP address type for an instance |
| `get-blueprints` | Instance | Get all available instance blueprints |
| `get-bundles` | Instance | Get all available instance bundles (sizes) |
| `get-regions` | Instance | Get all available AWS regions for Lightsail |
| `create-instance-snapshot` | Snapshot | Create a snapshot of an instance |
| `delete-instance-snapshot` | Snapshot | Delete an instance snapshot |
| `get-instance-snapshot` | Snapshot | Get details for an instance snapshot |
| `get-instance-snapshots` | Snapshot | Get all instance snapshots |
| `copy-snapshot` | Snapshot | Copy a snapshot to another region |
| `export-snapshot` | Snapshot | Export a snapshot to Amazon EC2 |
| `get-export-snapshot-records` | Snapshot | Get export snapshot records |
| `create-cloud-formation-stack` | Snapshot | Create EC2 resources from exported snapshot |
| `get-cloud-formation-stack-records` | Snapshot | Get CloudFormation stack records |
| `create-disk` | Disk | Create a block storage disk |
| `create-disk-from-snapshot` | Disk | Create a disk from a snapshot |
| `delete-disk` | Disk | Delete a disk |
| `get-disk` | Disk | Get details for a disk |
| `get-disks` | Disk | Get details for all disks |
| `attach-disk` | Disk | Attach a disk to an instance |
| `detach-disk` | Disk | Detach a disk from an instance |
| `create-disk-snapshot` | Disk | Create a snapshot of a disk |
| `delete-disk-snapshot` | Disk | Delete a disk snapshot |
| `get-disk-snapshot` | Disk | Get details for a disk snapshot |
| `get-disk-snapshots` | Disk | Get all disk snapshots |
| `get-auto-snapshots` | Disk | Get auto snapshot information |
| `delete-auto-snapshot` | Disk | Delete an auto snapshot |
| `enable-add-on` | Disk | Enable an add-on (auto snapshots) |
| `disable-add-on` | Disk | Disable an add-on |
| `create-load-balancer` | Load Balancer | Create a Lightsail load balancer |
| `delete-load-balancer` | Load Balancer | Delete a load balancer |
| `get-load-balancer` | Load Balancer | Get details for a load balancer |
| `get-load-balancers` | Load Balancer | Get all load balancers |
| `get-load-balancer-metric-data` | Load Balancer | Get load balancer metric data |
| `get-load-balancer-tls-certificates` | Load Balancer | Get TLS certificates for a load balancer |
| `get-load-balancer-tls-policies` | Load Balancer | Get available TLS security policies |
| `attach-instances-to-load-balancer` | Load Balancer | Attach instances to a load balancer |
| `detach-instances-from-load-balancer` | Load Balancer | Detach instances from a load balancer |
| `create-load-balancer-tls-certificate` | Load Balancer | Create a TLS certificate for a load balancer |
| `delete-load-balancer-tls-certificate` | Load Balancer | Delete a TLS certificate |
| `attach-load-balancer-tls-certificate` | Load Balancer | Attach a TLS certificate to a load balancer |
| `update-load-balancer-attribute` | Load Balancer | Update a load balancer attribute |
| `create-relational-database` | Database | Create a managed relational database |
| `create-relational-database-from-snapshot` | Database | Create a database from a snapshot |
| `delete-relational-database` | Database | Delete a managed database |
| `get-relational-database` | Database | Get details for a database |
| `get-relational-databases` | Database | Get all managed databases |
| `reboot-relational-database` | Database | Reboot a database |
| `start-relational-database` | Database | Start a stopped database |
| `stop-relational-database` | Database | Stop a running database |
| `update-relational-database` | Database | Update database settings |
| `update-relational-database-parameters` | Database | Update database parameters |
| `get-relational-database-parameters` | Database | Get database parameters |
| `get-relational-database-master-user-password` | Database | Get the master user password |
| `get-relational-database-metric-data` | Database | Get database metric data |
| `get-relational-database-events` | Database | Get database events |
| `get-relational-database-log-events` | Database | Get database log events |
| `get-relational-database-log-streams` | Database | Get database log streams |
| `get-relational-database-blueprints` | Database | Get available database engine versions |
| `get-relational-database-bundles` | Database | Get available database bundles |
| `create-relational-database-snapshot` | Database | Create a database snapshot |
| `delete-relational-database-snapshot` | Database | Delete a database snapshot |
| `get-relational-database-snapshot` | Database | Get details for a database snapshot |
| `get-relational-database-snapshots` | Database | Get all database snapshots |
| `create-container-service` | Container | Create a container service |
| `delete-container-service` | Container | Delete a container service |
| `get-container-services` | Container | Get all container services |
| `update-container-service` | Container | Update a container service |
| `create-container-service-deployment` | Container | Create a deployment for a container service |
| `get-container-service-deployments` | Container | Get deployments for a container service |
| `get-container-service-metric-data` | Container | Get container service metric data |
| `get-container-service-powers` | Container | Get available container service powers |
| `get-container-images` | Container | Get images for a container service |
| `delete-container-image` | Container | Delete a container image |
| `register-container-image` | Container | Register an image to a container service |
| `get-container-log` | Container | Get log events for a container |
| `create-distribution` | Distribution | Create a CDN distribution |
| `delete-distribution` | Distribution | Delete a distribution |
| `get-distributions` | Distribution | Get all distributions |
| `update-distribution` | Distribution | Update a distribution |
| `update-distribution-bundle` | Distribution | Update the distribution bundle |
| `get-distribution-bundles` | Distribution | Get available distribution bundles |
| `get-distribution-latest-cache-reset` | Distribution | Get latest cache reset timestamp |
| `get-distribution-metric-data` | Distribution | Get distribution metric data |
| `reset-distribution-cache` | Distribution | Reset the distribution cache |
| `attach-certificate-to-distribution` | Distribution | Attach a certificate to a distribution |
| `detach-certificate-from-distribution` | Distribution | Detach a certificate from a distribution |
| `create-domain` | Domain | Create a DNS domain |
| `delete-domain` | Domain | Delete a DNS domain |
| `get-domain` | Domain | Get details for a domain |
| `get-domains` | Domain | Get all domains |
| `create-domain-entry` | Domain | Create a DNS record |
| `update-domain-entry` | Domain | Update a DNS record |
| `delete-domain-entry` | Domain | Delete a DNS record |
| `create-bucket` | Bucket | Create an object storage bucket |
| `delete-bucket` | Bucket | Delete a bucket |
| `get-buckets` | Bucket | Get all buckets |
| `update-bucket` | Bucket | Update bucket settings |
| `update-bucket-bundle` | Bucket | Update the bucket bundle |
| `get-bucket-bundles` | Bucket | Get available bucket bundles |
| `get-bucket-access-keys` | Bucket | Get access keys for a bucket |
| `create-bucket-access-key` | Bucket | Create an access key for a bucket |
| `delete-bucket-access-key` | Bucket | Delete a bucket access key |
| `get-bucket-metric-data` | Bucket | Get bucket metric data |
| `set-resource-access-for-bucket` | Bucket | Set instance access to a bucket |
| `create-certificate` | Certificate | Create an SSL/TLS certificate |
| `delete-certificate` | Certificate | Delete a certificate |
| `get-certificates` | Certificate | Get all certificates |
| `allocate-static-ip` | Networking | Allocate a static IP address |
| `release-static-ip` | Networking | Release a static IP address |
| `get-static-ip` | Networking | Get details for a static IP |
| `get-static-ips` | Networking | Get all static IPs |
| `attach-static-ip` | Networking | Attach a static IP to an instance |
| `detach-static-ip` | Networking | Detach a static IP from an instance |
| `is-vpc-peered` | Networking | Check if VPCs are peered |
| `peer-vpc` | Networking | Peer the default VPC with the Lightsail VPC |
| `unpeer-vpc` | Networking | Unpeer the VPCs |
| `create-key-pair` | Key Pair | Create an SSH key pair |
| `delete-key-pair` | Key Pair | Delete a key pair |
| `get-key-pair` | Key Pair | Get details for a key pair |
| `get-key-pairs` | Key Pair | Get all key pairs |
| `import-key-pair` | Key Pair | Import a public key |
| `download-default-key-pair` | Key Pair | Download the default key pair |
| `delete-known-host-keys` | Key Pair | Delete known host keys for an instance |
| `put-alarm` | Alarm | Create or update an alarm |
| `delete-alarm` | Alarm | Delete an alarm |
| `get-alarms` | Alarm | Get all alarms |
| `test-alarm` | Alarm | Test an alarm notification |
| `create-contact-method` | Contact | Create a contact method for notifications |
| `delete-contact-method` | Contact | Delete a contact method |
| `get-contact-methods` | Contact | Get all contact methods |
| `send-contact-method-verification` | Contact | Send a verification for a contact method |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `get-cost-estimate` | Operations | Get cost estimate for a resource |
| `get-active-names` | Operations | Get all active resource names |
| `get-operation` | Operations | Get info about an operation |
| `get-operations` | Operations | Get info about all operations |
| `get-operations-for-resource` | Operations | Get operations for a specific resource |

---

## Global Options

These options are available on ALL `aws lightsail` commands.

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

### Operation Structure
Most Lightsail write operations return an `operations` array:
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Instance|StaticIp|Disk|...",
            "createdAt": "timestamp",
            "location": {
                "availabilityZone": "string",
                "regionName": "string"
            },
            "isTerminal": true|false,
            "operationType": "CreateInstance|DeleteInstance|...",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "statusChangedAt": "timestamp",
            "errorCode": "string",
            "errorDetails": "string"
        }
    ]
}
```

### Resource Types
`Instance`, `StaticIp`, `KeyPair`, `InstanceSnapshot`, `Domain`, `PeeredVpc`, `LoadBalancer`, `LoadBalancerTlsCertificate`, `Disk`, `DiskSnapshot`, `RelationalDatabase`, `RelationalDatabaseSnapshot`, `ExportSnapshotRecord`, `CloudFormationStackRecord`, `Alarm`, `ContactMethod`, `Distribution`, `Certificate`, `Bucket`, `ContainerService`

### Instance States
| State | Description |
|-------|-------------|
| `pending` | Instance is being created |
| `running` | Instance is running |
| `stopping` | Instance is stopping |
| `stopped` | Instance is stopped |
| `shutting-down` | Instance is shutting down |
| `terminated` | Instance is terminated |
