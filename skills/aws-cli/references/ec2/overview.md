# AWS CLI v2 — EC2 & Auto Scaling (ECS-Relevant)

## Overview

Reference for `aws ec2` and `aws autoscaling` subcommands relevant to deploying ECS on EC2. Scoped to infrastructure commands needed for ECS clusters — not the full 400+ EC2 command set.

## Quick Reference — Common Workflows

### Find latest ECS-optimized AMI
```bash
aws ec2 describe-images \
  --owners amazon \
  --filters "Name=name,Values=amzn2-ami-ecs-hvm-*-x86_64-ebs" \
  --query 'Images | sort_by(@, &CreationDate) | [-1].[ImageId,Name]' \
  --output text
```

### Create VPC + subnet for ECS
```bash
aws ec2 create-vpc --cidr-block 10.0.0.0/16 --query 'Vpc.VpcId' --output text
aws ec2 create-subnet --vpc-id vpc-xxx --cidr-block 10.0.1.0/24 --availability-zone us-east-1a
aws ec2 create-internet-gateway --query 'InternetGateway.InternetGatewayId' --output text
aws ec2 attach-internet-gateway --internet-gateway-id igw-xxx --vpc-id vpc-xxx
```

### Create security group for ECS
```bash
aws ec2 create-security-group --group-name ecs-sg --description "ECS instances" --vpc-id vpc-xxx
aws ec2 authorize-security-group-ingress --group-id sg-xxx --protocol tcp --port 80 --cidr 0.0.0.0/0
```

### Create launch template for ECS instances
```bash
aws ec2 create-launch-template --launch-template-name ecs-lt \
  --launch-template-data '{
    "ImageId":"ami-xxx",
    "InstanceType":"t3.medium",
    "IamInstanceProfile":{"Name":"ecsInstanceRole"},
    "UserData":"#!/bin/bash\necho ECS_CLUSTER=my-cluster >> /etc/ecs/ecs.config"
  }'
```

## Covered Command Groups

| Group | Commands | CLI Service |
|-------|----------|-------------|
| Instances | run, describe, terminate, start, stop, reboot | `aws ec2` |
| Security Groups | create, delete, describe, authorize/revoke ingress/egress | `aws ec2` |
| VPC | vpc, subnet, igw, route-table, nat-gateway, elastic-ip | `aws ec2` |
| Key Pairs | create, delete, describe, import | `aws ec2` |
| AMIs | describe-images | `aws ec2` |
| Launch Templates | create, delete, describe, versions, modify | `aws ec2` |
| Auto Scaling | create/delete/describe/update ASG, launch configurations | `aws autoscaling` |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Instances | [`instances.md`](instances.md) | run-instances, describe-instances, terminate-instances, start-instances, stop-instances, reboot-instances |
| Security Groups | [`security-groups.md`](security-groups.md) | create-security-group, delete-security-group, describe-security-groups, authorize-security-group-ingress, authorize-security-group-egress, revoke-security-group-ingress, revoke-security-group-egress |
| VPC | [`vpc.md`](vpc.md) | create-vpc, delete-vpc, describe-vpcs, modify-vpc-attribute, create-subnet, delete-subnet, describe-subnets, create-internet-gateway, delete-internet-gateway, attach-internet-gateway, detach-internet-gateway, describe-internet-gateways, create-route-table, delete-route-table, describe-route-tables, create-route, delete-route, associate-route-table, disassociate-route-table, create-nat-gateway, delete-nat-gateway, describe-nat-gateways, allocate-address, release-address, describe-addresses |
| Key Pairs | [`key-pairs.md`](key-pairs.md) | create-key-pair, delete-key-pair, describe-key-pairs, import-key-pair |
| AMIs | [`amis.md`](amis.md) | describe-images |
| Launch Templates | [`launch-templates.md`](launch-templates.md) | create-launch-template, delete-launch-template, describe-launch-templates, describe-launch-template-versions, create-launch-template-version, modify-launch-template |
| Auto Scaling | [`auto-scaling.md`](auto-scaling.md) | create-auto-scaling-group, delete-auto-scaling-group, describe-auto-scaling-groups, update-auto-scaling-group, create-launch-configuration, delete-launch-configuration, describe-launch-configurations |
