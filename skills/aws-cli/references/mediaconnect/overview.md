# AWS CLI v2 — MediaConnect

## Overview

Complete reference for all `aws mediaconnect` subcommands in AWS CLI v2. Covers flow management, sources, outputs, entitlements, media streams, VPC interfaces, bridges, gateways, routers, reservations, and resource tagging. AWS Elemental MediaConnect is a reliable, secure, and flexible transport service for live video that enables broadcasters and content owners to build real-time video workflows.

## Quick Reference — Common Workflows

### Create a flow with a source
```bash
aws mediaconnect create-flow \
    --name MyLiveFlow \
    --source Name=PrimarySource,Protocol=rtp,IngestPort=5000,WhitelistCidr=10.0.0.0/16
```

### Add an output to a flow
```bash
aws mediaconnect add-flow-outputs \
    --flow-arn arn:aws:mediaconnect:us-east-1:123456789012:flow:1-abc123:MyFlow \
    --outputs Name=OutputNYC,Protocol=rtp-fec,Destination=192.0.2.12,Port=5001,SmoothingLatency=100
```

### Start and stop a flow
```bash
aws mediaconnect start-flow \
    --flow-arn arn:aws:mediaconnect:us-east-1:123456789012:flow:1-abc123:MyFlow

aws mediaconnect stop-flow \
    --flow-arn arn:aws:mediaconnect:us-east-1:123456789012:flow:1-abc123:MyFlow
```

### Grant an entitlement to share content
```bash
aws mediaconnect grant-flow-entitlements \
    --flow-arn arn:aws:mediaconnect:us-east-1:123456789012:flow:1-abc123:MyFlow \
    --entitlements Name=PartnerEntitlement,Subscribers=444455556666,Description='Partner access'
```

### Create a bridge for hybrid workflows
```bash
aws mediaconnect create-bridge \
    --name MyBridge \
    --placement-arn arn:aws:mediaconnect:us-east-1:123456789012:gateway:1-abc123:MyGateway \
    --sources FlowSource={FlowArn=arn:aws:mediaconnect:us-east-1:123456789012:flow:1-abc123:MyFlow,Name=BridgeSource} \
    --egress-gateway-bridge MaxBitrate=80000000
```

### Create a gateway
```bash
aws mediaconnect create-gateway \
    --name MyGateway \
    --egress-cidr-blocks 10.0.0.0/16 \
    --networks CidrBlock=192.168.0.0/24,Name=network1
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Flows | [flows.md](flows.md) | `create-flow`, `describe-flow`, `list-flows`, `update-flow`, `delete-flow`, `start-flow`, `stop-flow`, `describe-flow-source-metadata`, `describe-flow-source-thumbnail` |
| Sources | [sources.md](sources.md) | `add-flow-sources`, `update-flow-source`, `remove-flow-source` |
| Outputs | [outputs.md](outputs.md) | `add-flow-outputs`, `update-flow-output`, `remove-flow-output` |
| Entitlements | [entitlements.md](entitlements.md) | `grant-flow-entitlements`, `update-flow-entitlement`, `revoke-flow-entitlement`, `list-entitlements` |
| Media Streams | [media-streams.md](media-streams.md) | `add-flow-media-streams`, `update-flow-media-stream`, `remove-flow-media-stream` |
| VPC Interfaces | [vpc-interfaces.md](vpc-interfaces.md) | `add-flow-vpc-interfaces`, `remove-flow-vpc-interface` |
| Bridges | [bridges.md](bridges.md) | `create-bridge`, `describe-bridge`, `list-bridges`, `update-bridge`, `update-bridge-state`, `delete-bridge`, `add-bridge-sources`, `update-bridge-source`, `remove-bridge-source`, `add-bridge-outputs`, `update-bridge-output`, `remove-bridge-output` |
| Gateways | [gateways.md](gateways.md) | `create-gateway`, `describe-gateway`, `list-gateways`, `delete-gateway`, `describe-gateway-instance`, `list-gateway-instances`, `update-gateway-instance`, `deregister-gateway-instance` |
| Routers | [routers.md](routers.md) | `create-router-input`, `get-router-input`, `list-router-inputs`, `update-router-input`, `delete-router-input`, `start-router-input`, `stop-router-input`, `restart-router-input`, `take-router-input`, `batch-get-router-input`, `get-router-input-source-metadata`, `get-router-input-thumbnail`, `create-router-output`, `get-router-output`, `list-router-outputs`, `update-router-output`, `delete-router-output`, `start-router-output`, `stop-router-output`, `restart-router-output`, `batch-get-router-output`, `create-router-network-interface`, `get-router-network-interface`, `list-router-network-interfaces`, `update-router-network-interface`, `delete-router-network-interface`, `batch-get-router-network-interface` |
| Reservations | [reservations.md](reservations.md) | `list-offerings`, `describe-offering`, `purchase-offering`, `list-reservations`, `describe-reservation` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource`, `tag-global-resource`, `untag-global-resource`, `list-tags-for-global-resource` |
