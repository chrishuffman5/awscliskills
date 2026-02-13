# AWS CLI v2 — MSK (Amazon Managed Streaming for Apache Kafka)

## Overview

Complete reference for `aws kafka` and `aws kafkaconnect` subcommands in AWS CLI v2. Covers MSK cluster management (provisioned and serverless), broker configuration, topic management, replication, VPC connectivity, SCRAM authentication, cluster policies, and Kafka Connect connectors/plugins/workers.

## Quick Reference — Common Workflows

### Create a provisioned MSK cluster
```bash
aws kafka create-cluster \
  --cluster-name my-cluster \
  --broker-node-group-info file://broker-info.json \
  --kafka-version "3.6.0" \
  --number-of-broker-nodes 3
```

### Create a serverless MSK cluster
```bash
aws kafka create-cluster-v2 \
  --cluster-name my-serverless-cluster \
  --serverless '{"VpcConfigs":[{"SubnetIds":["subnet-abc","subnet-def"],"SecurityGroupIds":["sg-123"]}],"ClientAuthentication":{"Sasl":{"Iam":{"Enabled":true}}}}'
```

### Get bootstrap broker endpoints
```bash
aws kafka get-bootstrap-brokers --cluster-arn arn:aws:kafka:us-east-1:123456789012:cluster/my-cluster/abc-123
```

### Create and apply a configuration
```bash
aws kafka create-configuration \
  --name my-config \
  --kafka-versions "3.6.0" \
  --server-properties fileb://server.properties

aws kafka update-cluster-configuration \
  --cluster-arn arn:aws:kafka:... \
  --current-version K1 \
  --configuration-info '{"Arn":"arn:aws:kafka:...:configuration/my-config/abc","Revision":1}'
```

### Create a topic
```bash
aws kafka create-topic \
  --cluster-arn arn:aws:kafka:... \
  --topic-name my-topic \
  --partition-count 6 \
  --replication-factor 3
```

### Set up cross-cluster replication
```bash
aws kafka create-replicator \
  --replicator-name my-replicator \
  --service-execution-role-arn arn:aws:iam::123456789012:role/MSKReplicatorRole \
  --kafka-clusters file://kafka-clusters.json \
  --replication-info-list file://replication-info.json
```

### Associate SCRAM secrets for authentication
```bash
aws kafka batch-associate-scram-secret \
  --cluster-arn arn:aws:kafka:... \
  --secret-arn-list arn:aws:secretsmanager:us-east-1:123456789012:secret:AmazonMSK_user1
```

### Create a Kafka Connect connector
```bash
aws kafkaconnect create-connector \
  --connector-name my-s3-sink \
  --kafka-connect-version "2.7.1" \
  --plugins '[{"customPlugin":{"customPluginArn":"arn:aws:kafkaconnect:...","revision":1}}]' \
  --connector-configuration file://connector-config.json \
  --capacity '{"provisionedCapacity":{"mcuCount":1,"workerCount":2}}' \
  --kafka-cluster file://kafka-cluster.json \
  --kafka-cluster-client-authentication '{"authenticationType":"IAM"}' \
  --kafka-cluster-encryption-in-transit '{"encryptionType":"TLS"}' \
  --service-execution-role-arn arn:aws:iam::123456789012:role/KafkaConnectRole
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Clusters | [`clusters.md`](clusters.md) | create-cluster, create-cluster-v2, delete-cluster, describe-cluster, describe-cluster-v2, list-clusters, list-clusters-v2, get-bootstrap-brokers, get-compatible-kafka-versions, list-kafka-versions |
| Configuration | [`configuration.md`](configuration.md) | create-configuration, delete-configuration, describe-configuration, describe-configuration-revision, list-configurations, list-configuration-revisions, update-cluster-configuration, update-cluster-kafka-version, update-monitoring, update-rebalancing |
| Topics | [`topics.md`](topics.md) | create-topic, delete-topic, describe-topic, describe-topic-partitions, list-topics, update-topic |
| Broker Management | [`broker-management.md`](broker-management.md) | update-broker-count, update-broker-storage, update-broker-type, update-storage, reboot-broker, list-nodes, update-connectivity, update-security |
| Replicators | [`replicators.md`](replicators.md) | create-replicator, delete-replicator, describe-replicator, list-replicators, update-replication-info |
| VPC Connections | [`vpc-connections.md`](vpc-connections.md) | create-vpc-connection, delete-vpc-connection, describe-vpc-connection, list-vpc-connections, list-client-vpc-connections, reject-client-vpc-connection |
| SCRAM Secrets | [`scram-secrets.md`](scram-secrets.md) | batch-associate-scram-secret, batch-disassociate-scram-secret, list-scram-secrets |
| Operations & Policies | [`operations-policies.md`](operations-policies.md) | describe-cluster-operation, describe-cluster-operation-v2, list-cluster-operations, list-cluster-operations-v2, get-cluster-policy, put-cluster-policy, delete-cluster-policy, tag-resource, untag-resource, list-tags-for-resource |
| Connect Connectors | [`connect-connectors.md`](connect-connectors.md) | create-connector, delete-connector, describe-connector, list-connectors, update-connector, describe-connector-operation, list-connector-operations |
| Connect Plugins & Workers | [`connect-plugins-workers.md`](connect-plugins-workers.md) | create-custom-plugin, delete-custom-plugin, describe-custom-plugin, list-custom-plugins, create-worker-configuration, delete-worker-configuration, describe-worker-configuration, list-worker-configurations, tag-resource, untag-resource, list-tags-for-resource |
