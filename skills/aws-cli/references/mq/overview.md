# AWS CLI v2 — Amazon MQ

## Overview

Complete reference for all `aws mq` subcommands in AWS CLI v2. Covers broker lifecycle management, configuration management, user management, and resource tagging. Amazon MQ is a managed message broker service for Apache ActiveMQ and RabbitMQ that makes it easy to set up and operate message brokers in the cloud with support for industry-standard messaging protocols (AMQP, MQTT, OpenWire, STOMP, WSS).

## Quick Reference — Common Workflows

### Create an ActiveMQ broker with a user
```bash
aws mq create-broker \
    --broker-name my-activemq-broker \
    --engine-type ACTIVEMQ \
    --engine-version "5.18" \
    --host-instance-type mq.m5.large \
    --deployment-mode SINGLE_INSTANCE \
    --publicly-accessible \
    --users '[{"Username":"admin","Password":"MyStr0ngP@ssw0rd","ConsoleAccess":true,"Groups":["admin"]}]' \
    --subnet-ids subnet-abc123 \
    --security-groups sg-abc123
```

### Create a RabbitMQ cluster broker
```bash
aws mq create-broker \
    --broker-name my-rabbitmq-cluster \
    --engine-type RABBITMQ \
    --engine-version "3.13" \
    --host-instance-type mq.m5.large \
    --deployment-mode CLUSTER_MULTI_AZ \
    --no-publicly-accessible \
    --users '[{"Username":"admin","Password":"MyStr0ngP@ssw0rd"}]' \
    --subnet-ids subnet-abc123 subnet-def456 subnet-ghi789 \
    --security-groups sg-abc123
```

### Create and apply a configuration
```bash
aws mq create-configuration \
    --name my-activemq-config \
    --engine-type ACTIVEMQ \
    --engine-version "5.18"

# Update configuration with XML data (base64-encoded)
aws mq update-configuration \
    --configuration-id c-abc123 \
    --data "PD94bWwgdmVyc2lvbj0i..." \
    --description "Enable advisory topics"

# Apply configuration to broker
aws mq update-broker \
    --broker-id b-abc123 \
    --configuration '{"Id":"c-abc123","Revision":2}'
```

### Manage broker users
```bash
aws mq create-user \
    --broker-id b-abc123 \
    --username appuser \
    --password "MyStr0ngP@ssw0rd" \
    --console-access \
    --groups "developers" "readers"

aws mq list-users --broker-id b-abc123

# Reboot required to apply user changes
aws mq reboot-broker --broker-id b-abc123
```

### Monitor broker status
```bash
aws mq describe-broker --broker-id b-abc123 \
    --query '{State:BrokerState,Engine:EngineType,Version:EngineVersion,Instances:BrokerInstances[].Endpoints}'

aws mq list-brokers \
    --query 'BrokerSummaries[].{Name:BrokerName,Id:BrokerId,State:BrokerState,Engine:EngineType}'
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Brokers | [brokers.md](brokers.md) | `create-broker`, `describe-broker`, `list-brokers`, `update-broker`, `delete-broker`, `reboot-broker`, `promote`, `describe-broker-engine-types`, `describe-broker-instance-options` |
| Configurations | [configurations.md](configurations.md) | `create-configuration`, `describe-configuration`, `list-configurations`, `update-configuration`, `delete-configuration`, `describe-configuration-revision`, `list-configuration-revisions` |
| Users | [users.md](users.md) | `create-user`, `describe-user`, `list-users`, `update-user`, `delete-user` |
| Tags | [tags.md](tags.md) | `create-tags`, `list-tags`, `delete-tags` |
