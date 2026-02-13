# AWS CLI v2 — OpenSearch (Service + Serverless)

## Overview

Complete reference for `aws opensearch` and `aws opensearchserverless` subcommands in AWS CLI v2. Covers OpenSearch Service domain management (provisioned clusters, EBS, VPC, security, upgrades, packages, connections, data sources, indexes, applications) and OpenSearch Serverless (collections, security/access/lifecycle policies, VPC endpoints, indexes).

## Quick Reference — Common Workflows

### Create a domain
```bash
aws opensearch create-domain \
  --domain-name my-domain \
  --engine-version OpenSearch_2.11 \
  --cluster-config InstanceType=r6g.large.search,InstanceCount=3,DedicatedMasterEnabled=true,DedicatedMasterType=r6g.large.search,DedicatedMasterCount=3,ZoneAwarenessEnabled=true,ZoneAwarenessConfig={AvailabilityZoneCount=3} \
  --ebs-options EBSEnabled=true,VolumeType=gp3,VolumeSize=100 \
  --encryption-at-rest-options Enabled=true \
  --node-to-node-encryption-options Enabled=true \
  --domain-endpoint-options EnforceHTTPS=true,TLSSecurityPolicy=Policy-Min-TLS-1-2-2019-07 \
  --advanced-security-options Enabled=true,InternalUserDatabaseEnabled=true,MasterUserOptions='{MasterUserName=admin,MasterUserPassword=MyP@ssw0rd!}'
```

### Describe a domain
```bash
aws opensearch describe-domain --domain-name my-domain \
  --query 'DomainStatus.{Endpoint:Endpoint,Status:DomainProcessingStatus,Engine:EngineVersion}'
```

### Update domain configuration
```bash
aws opensearch update-domain-config --domain-name my-domain \
  --cluster-config InstanceType=r6g.xlarge.search,InstanceCount=6
```

### Upgrade domain engine version
```bash
aws opensearch upgrade-domain --domain-name my-domain \
  --target-version OpenSearch_2.13
aws opensearch get-upgrade-status --domain-name my-domain
```

### Create a serverless collection
```bash
# First create encryption policy
aws opensearchserverless create-security-policy \
  --name my-encryption-policy --type encryption \
  --policy '{"Rules":[{"Resource":["collection/my-collection"],"ResourceType":"collection"}],"AWSOwnedKey":true}'

# Then create network policy
aws opensearchserverless create-security-policy \
  --name my-network-policy --type network \
  --policy '[{"Rules":[{"Resource":["collection/my-collection"],"ResourceType":"collection"}],"AllowFromPublic":true}]'

# Create the collection
aws opensearchserverless create-collection \
  --name my-collection --type SEARCH
```

### Create a serverless access policy
```bash
aws opensearchserverless create-access-policy \
  --name my-access-policy --type data \
  --policy '[{"Rules":[{"Resource":["collection/my-collection"],"Permission":["aoss:CreateCollectionItems","aoss:UpdateCollectionItems","aoss:DescribeCollectionItems"],"ResourceType":"collection"},{"Resource":["index/my-collection/*"],"Permission":["aoss:CreateIndex","aoss:UpdateIndex","aoss:DescribeIndex","aoss:ReadDocument","aoss:WriteDocument"],"ResourceType":"index"}],"Principal":["arn:aws:iam::123456789012:role/my-role"]}]'
```

### Create a cross-cluster connection
```bash
aws opensearch create-outbound-connection \
  --local-domain-info '{DomainName:source-domain,Region:us-east-1,OwnerId:123456789012}' \
  --remote-domain-info '{DomainName:dest-domain,Region:us-west-2,OwnerId:123456789012}' \
  --connection-alias my-connection
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Domains | [`domains.md`](domains.md) | create-domain, delete-domain, describe-domain, describe-domains, describe-domain-config, update-domain-config, list-domain-names, describe-domain-health, describe-domain-nodes, describe-domain-auto-tunes, describe-domain-change-progress, cancel-domain-config-change, describe-instance-type-limits, list-instance-type-details, get-compatible-versions, list-versions, describe-reserved-instances, describe-reserved-instance-offerings, purchase-reserved-instance-offering |
| Upgrades | [`upgrades.md`](upgrades.md) | upgrade-domain, get-upgrade-status, get-upgrade-history, start-service-software-update, cancel-service-software-update, list-scheduled-actions, update-scheduled-action |
| Packages | [`packages.md`](packages.md) | create-package, delete-package, update-package, describe-packages, associate-package, dissociate-package, get-package-version-history, list-domains-for-package, list-packages-for-domain |
| Connections | [`connections.md`](connections.md) | create-outbound-connection, delete-outbound-connection, describe-outbound-connections, accept-inbound-connection, delete-inbound-connection, describe-inbound-connections, reject-inbound-connection |
| VPC Endpoints | [`vpc-endpoints.md`](vpc-endpoints.md) | create-vpc-endpoint, delete-vpc-endpoint, describe-vpc-endpoints, list-vpc-endpoints-for-domain, authorize-vpc-endpoint-access, revoke-vpc-endpoint-access, list-vpc-endpoint-access, update-vpc-endpoint |
| Applications | [`applications.md`](applications.md) | create-application, delete-application, update-application, get-application, list-applications |
| Indexes | [`indexes.md`](indexes.md) | create-index, delete-index, get-index, update-index |
| Data Sources | [`data-sources.md`](data-sources.md) | add-data-source, delete-data-source, get-data-source, list-data-sources, update-data-source, add-direct-query-data-source, delete-direct-query-data-source, get-direct-query-data-source, list-direct-query-data-sources, update-direct-query-data-source |
| Maintenance | [`maintenance.md`](maintenance.md) | start-domain-maintenance, get-domain-maintenance-status, list-domain-maintenances, describe-dry-run-progress, add-tags, remove-tags, list-tags |
| Serverless Collections | [`serverless-collections.md`](serverless-collections.md) | create-collection, delete-collection, batch-get-collection, list-collections, update-collection, create-collection-group, delete-collection-group, batch-get-collection-group, list-collection-groups, update-collection-group |
| Serverless Security | [`serverless-security.md`](serverless-security.md) | create-security-policy, delete-security-policy, get-security-policy, list-security-policies, update-security-policy, create-access-policy, delete-access-policy, get-access-policy, list-access-policies, update-access-policy, create-security-config, delete-security-config, get-security-config, list-security-configs, update-security-config |
| Serverless VPC | [`serverless-vpc.md`](serverless-vpc.md) | create-vpc-endpoint, delete-vpc-endpoint, batch-get-vpc-endpoint, list-vpc-endpoints, update-vpc-endpoint |
| Serverless Lifecycle | [`serverless-lifecycle.md`](serverless-lifecycle.md) | create-lifecycle-policy, delete-lifecycle-policy, batch-get-lifecycle-policy, batch-get-effective-lifecycle-policy, list-lifecycle-policies, update-lifecycle-policy |
| Serverless Indexes & Settings | [`serverless-indexes-settings.md`](serverless-indexes-settings.md) | create-index, delete-index, get-index, update-index, get-account-settings, update-account-settings, get-policies-stats, tag-resource, untag-resource, list-tags-for-resource |
