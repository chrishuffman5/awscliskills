# AWS CLI v2 — Network Manager

## Overview

Complete reference for all `aws networkmanager` subcommands in AWS CLI v2. Covers global network management, core networks (AWS Cloud WAN), sites, devices, links, connections, Transit Gateway integration, VPC/VPN/Connect/Direct Connect attachments, Connect peers, peerings, route analysis, and organization service access.

## Quick Reference — Common Workflows

### Create a global network and core network
```bash
# Create global network
aws networkmanager create-global-network \
  --description "Production network" \
  --tags Key=Env,Value=prod \
  --region us-west-2

# Create core network with policy
aws networkmanager create-core-network \
  --global-network-id global-network-0abc123 \
  --policy-document file://core-network-policy.json \
  --region us-west-2
```

### Register a site and device
```bash
# Create a site
aws networkmanager create-site \
  --global-network-id global-network-0abc123 \
  --description "NYC Office" \
  --location Latitude=40.7128,Longitude=-74.0060 \
  --region us-west-2

# Create a device
aws networkmanager create-device \
  --global-network-id global-network-0abc123 \
  --site-id site-0abc123 \
  --description "NYC Router" \
  --vendor "Cisco" --model "ISR 4000" \
  --region us-west-2
```

### Attach a VPC to a core network
```bash
aws networkmanager create-vpc-attachment \
  --core-network-id core-network-0abc123 \
  --vpc-arn arn:aws:ec2:us-east-1:123456789012:vpc/vpc-0abc123 \
  --subnet-arns arn:aws:ec2:us-east-1:123456789012:subnet/subnet-0abc123 \
  --region us-west-2

# Accept the attachment
aws networkmanager accept-attachment \
  --attachment-id attachment-0abc123 \
  --region us-west-2
```

### Register and associate a Transit Gateway
```bash
aws networkmanager register-transit-gateway \
  --global-network-id global-network-0abc123 \
  --transit-gateway-arn arn:aws:ec2:us-east-1:123456789012:transit-gateway/tgw-0abc123 \
  --region us-west-2
```

### Run a route analysis
```bash
aws networkmanager start-route-analysis \
  --global-network-id global-network-0abc123 \
  --source TransitGatewayAttachmentArn=arn:aws:ec2:us-east-1:123456789012:transit-gateway-attachment/tgw-attach-0abc,IpAddress=10.0.0.1 \
  --destination TransitGatewayAttachmentArn=arn:aws:ec2:us-west-2:123456789012:transit-gateway-attachment/tgw-attach-0def,IpAddress=10.1.0.1 \
  --include-return-path \
  --region us-west-2
```

### Update core network policy
```bash
aws networkmanager put-core-network-policy \
  --core-network-id core-network-0abc123 \
  --policy-document file://updated-policy.json \
  --region us-west-2

# Execute the change set
aws networkmanager execute-core-network-change-set \
  --core-network-id core-network-0abc123 \
  --policy-version-id 2 \
  --region us-west-2
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Global Networks | [`global-networks.md`](global-networks.md) | create-global-network, delete-global-network, describe-global-networks, update-global-network |
| Core Networks | [`core-networks.md`](core-networks.md) | create-core-network, delete-core-network, get-core-network, list-core-networks, update-core-network, put-core-network-policy, get-core-network-policy, get-core-network-change-set, get-core-network-change-events, execute-core-network-change-set, list-core-network-policy-versions, delete-core-network-policy-version, restore-core-network-policy-version |
| Core Network Prefixes | [`core-network-prefixes.md`](core-network-prefixes.md) | create-core-network-prefix-list-association, delete-core-network-prefix-list-association, list-core-network-prefix-list-associations, list-core-network-routing-information |
| Sites, Devices & Links | [`sites-devices-links.md`](sites-devices-links.md) | create-site, delete-site, get-sites, update-site, create-device, delete-device, get-devices, update-device, create-link, delete-link, get-links, update-link, associate-link, disassociate-link, get-link-associations |
| Connections | [`connections.md`](connections.md) | create-connection, delete-connection, get-connections, update-connection |
| Transit Gateway | [`transit-gateway.md`](transit-gateway.md) | register-transit-gateway, deregister-transit-gateway, get-transit-gateway-registrations, associate-transit-gateway-connect-peer, disassociate-transit-gateway-connect-peer, get-transit-gateway-connect-peer-associations, create-transit-gateway-peering, get-transit-gateway-peering, create-transit-gateway-route-table-attachment, get-transit-gateway-route-table-attachment |
| Attachments | [`attachments.md`](attachments.md) | create-vpc-attachment, update-vpc-attachment, get-vpc-attachment, create-connect-attachment, get-connect-attachment, create-site-to-site-vpn-attachment, get-site-to-site-vpn-attachment, create-direct-connect-gateway-attachment, get-direct-connect-gateway-attachment, update-direct-connect-gateway-attachment, accept-attachment, reject-attachment, delete-attachment, list-attachments |
| Connect Peers | [`connect-peers.md`](connect-peers.md) | create-connect-peer, delete-connect-peer, get-connect-peer, list-connect-peers, associate-connect-peer, disassociate-connect-peer, get-connect-peer-associations |
| Customer Gateway | [`customer-gateway.md`](customer-gateway.md) | associate-customer-gateway, disassociate-customer-gateway, get-customer-gateway-associations |
| Peerings | [`peerings.md`](peerings.md) | create-transit-gateway-peering, get-transit-gateway-peering, list-peerings |
| Route Analysis | [`route-analysis.md`](route-analysis.md) | start-route-analysis, get-route-analysis, get-network-routes, get-network-resources, get-network-resource-counts, get-network-resource-relationships, get-network-telemetry, update-network-resource-metadata, list-attachment-routing-policy-associations, put-attachment-routing-policy-label, remove-attachment-routing-policy-label |
| Organizations | [`organizations.md`](organizations.md) | list-organization-service-access-status, start-organization-service-access-update |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource, get-resource-policy, put-resource-policy, delete-resource-policy |
