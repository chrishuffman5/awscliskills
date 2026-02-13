# AWS CLI v2 — Global Accelerator

## Overview

Complete reference for all `aws globalaccelerator` subcommands in AWS CLI v2. AWS Global Accelerator is a networking service that improves application availability and performance by directing traffic through the AWS global network. Supports standard accelerators (automatic traffic routing) and custom routing accelerators (deterministic routing to specific EC2 instances). Also covers BYOIP (Bring Your Own IP) and cross-account resource sharing.

**Important:** Global Accelerator is a global service. You must specify `--region us-west-2` for all accelerator operations.

## Quick Reference — Common Workflows

### Create a standard accelerator with listener and endpoint group
```bash
aws globalaccelerator create-accelerator \
  --name my-accelerator \
  --region us-west-2

aws globalaccelerator create-listener \
  --accelerator-arn arn:aws:globalaccelerator::123456789012:accelerator/abc123 \
  --port-ranges FromPort=80,ToPort=80 FromPort=443,ToPort=443 \
  --protocol TCP \
  --region us-west-2

aws globalaccelerator create-endpoint-group \
  --listener-arn arn:aws:globalaccelerator::123456789012:accelerator/abc123/listener/def456 \
  --endpoint-group-region us-east-1 \
  --endpoint-configurations EndpointId=arn:aws:elasticloadbalancing:us-east-1:123456789012:loadbalancer/app/my-alb/abc123,Weight=128 \
  --region us-west-2
```

### Add endpoints to an endpoint group
```bash
aws globalaccelerator add-endpoints \
  --endpoint-group-arn arn:aws:globalaccelerator::123456789012:accelerator/abc123/listener/def456/endpoint-group/ghi789 \
  --endpoint-configurations EndpointId=i-1234567890abcdef0,Weight=128 \
  --region us-west-2
```

### Enable flow logs
```bash
aws globalaccelerator update-accelerator-attributes \
  --accelerator-arn arn:aws:globalaccelerator::123456789012:accelerator/abc123 \
  --flow-logs-enabled \
  --flow-logs-s3-bucket my-flow-logs-bucket \
  --flow-logs-s3-prefix accelerator-logs/ \
  --region us-west-2
```

### Create a custom routing accelerator
```bash
aws globalaccelerator create-custom-routing-accelerator \
  --name my-custom-accelerator \
  --region us-west-2

aws globalaccelerator create-custom-routing-listener \
  --accelerator-arn arn:aws:globalaccelerator::123456789012:accelerator/abc123 \
  --port-ranges FromPort=10000,ToPort=20000 \
  --region us-west-2

aws globalaccelerator create-custom-routing-endpoint-group \
  --listener-arn arn:aws:globalaccelerator::123456789012:accelerator/abc123/listener/def456 \
  --endpoint-group-region us-east-1 \
  --destination-configurations "FromPort=80,ToPort=8080,Protocols=TCP,UDP" \
  --region us-west-2
```

### Allow traffic to custom routing endpoints
```bash
aws globalaccelerator allow-custom-routing-traffic \
  --endpoint-group-arn arn:aws:globalaccelerator::123456789012:accelerator/abc123/listener/def456/endpoint-group/ghi789 \
  --endpoint-id subnet-abcd1234 \
  --destination-addresses "172.31.200.6" "172.31.200.7" \
  --destination-ports 80 443 \
  --region us-west-2
```

### Provision BYOIP address range
```bash
aws globalaccelerator provision-byoip-cidr \
  --cidr 198.51.100.0/24 \
  --cidr-authorization-context Message="$TEXT_MESSAGE",Signature="$SIGNED_MESSAGE" \
  --region us-west-2

aws globalaccelerator advertise-byoip-cidr \
  --cidr 198.51.100.0/24 \
  --region us-west-2
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Accelerators | [`accelerators.md`](accelerators.md) | create-accelerator, delete-accelerator, describe-accelerator, list-accelerators, update-accelerator, describe-accelerator-attributes, update-accelerator-attributes |
| Listeners | [`listeners.md`](listeners.md) | create-listener, delete-listener, describe-listener, list-listeners, update-listener |
| Endpoint Groups | [`endpoint-groups.md`](endpoint-groups.md) | create-endpoint-group, delete-endpoint-group, describe-endpoint-group, list-endpoint-groups, update-endpoint-group, add-endpoints, remove-endpoints |
| Custom Routing | [`custom-routing.md`](custom-routing.md) | create-custom-routing-accelerator, delete-custom-routing-accelerator, describe-custom-routing-accelerator, list-custom-routing-accelerators, update-custom-routing-accelerator, describe-custom-routing-accelerator-attributes, update-custom-routing-accelerator-attributes, create-custom-routing-listener, delete-custom-routing-listener, describe-custom-routing-listener, list-custom-routing-listeners, update-custom-routing-listener, create-custom-routing-endpoint-group, delete-custom-routing-endpoint-group, describe-custom-routing-endpoint-group, list-custom-routing-endpoint-groups, add-custom-routing-endpoints, remove-custom-routing-endpoints, allow-custom-routing-traffic, deny-custom-routing-traffic, list-custom-routing-port-mappings, list-custom-routing-port-mappings-by-destination |
| Cross-Account | [`cross-account.md`](cross-account.md) | create-cross-account-attachment, delete-cross-account-attachment, describe-cross-account-attachment, list-cross-account-attachments, update-cross-account-attachment, list-cross-account-resource-accounts, list-cross-account-resources |
| BYOIP | [`byoip.md`](byoip.md) | provision-byoip-cidr, deprovision-byoip-cidr, advertise-byoip-cidr, withdraw-byoip-cidr, list-byoip-cidrs |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
