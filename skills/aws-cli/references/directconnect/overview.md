# AWS CLI v2 — Direct Connect

## Overview

Complete reference for all `aws directconnect` subcommands in AWS CLI v2. Covers dedicated connections, Direct Connect gateways, virtual interfaces (private, public, transit), link aggregation groups (LAGs), BGP peering, MACsec encryption, interconnects (partner), and resource tagging.

## Quick Reference — Common Workflows

### Create a dedicated connection
```bash
aws directconnect create-connection \
  --location EqDC2 \
  --bandwidth 1Gbps \
  --connection-name "DC-to-AWS-Primary"
```

### Create a Direct Connect gateway
```bash
aws directconnect create-direct-connect-gateway \
  --direct-connect-gateway-name my-dx-gateway \
  --amazon-side-asn 64512
```

### Associate gateway with a transit gateway
```bash
aws directconnect create-direct-connect-gateway-association \
  --direct-connect-gateway-id dxgw-abcdef01 \
  --gateway-id tgw-12345678 \
  --add-allowed-prefixes-to-direct-connect-gateway cidr=10.0.0.0/8
```

### Create a private virtual interface
```bash
aws directconnect create-private-virtual-interface \
  --connection-id dxcon-fg31dyv6 \
  --new-private-virtual-interface \
    virtualInterfaceName=my-private-vif,vlan=101,asn=65000,directConnectGatewayId=dxgw-abcdef01,addressFamily=ipv4
```

### Create a transit virtual interface
```bash
aws directconnect create-transit-virtual-interface \
  --connection-id dxcon-fg31dyv6 \
  --new-transit-virtual-interface \
    virtualInterfaceName=my-transit-vif,vlan=200,asn=65100,directConnectGatewayId=dxgw-abcdef01,addressFamily=ipv4
```

### Create a LAG and associate a connection
```bash
aws directconnect create-lag \
  --location EqDC2 \
  --number-of-connections 2 \
  --connections-bandwidth 10Gbps \
  --lag-name "Primary-LAG"

aws directconnect associate-connection-with-lag \
  --connection-id dxcon-fg31dyv6 \
  --lag-id dxlag-ffrhowd9
```

### Enable MACsec on a connection
```bash
aws directconnect associate-mac-sec-key \
  --connection-id dxcon-fg31dyv6 \
  --secret-arn arn:aws:secretsmanager:us-east-1:123456789012:secret:my-macsec-key

aws directconnect update-connection \
  --connection-id dxcon-fg31dyv6 \
  --encryption-mode must_encrypt
```

### List all connections and virtual interfaces
```bash
aws directconnect describe-connections --query 'connections[].{ID:connectionId,Name:connectionName,State:connectionState}'
aws directconnect describe-virtual-interfaces --query 'virtualInterfaces[].{ID:virtualInterfaceId,Type:virtualInterfaceType,State:virtualInterfaceState}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Connections | [`connections.md`](connections.md) | create-connection, delete-connection, describe-connections, update-connection, confirm-connection, allocate-hosted-connection, describe-hosted-connections, associate-hosted-connection, associate-connection-with-lag, disassociate-connection-from-lag, describe-loa, describe-locations, describe-customer-metadata, confirm-customer-agreement |
| Gateways | [`gateways.md`](gateways.md) | create-direct-connect-gateway, delete-direct-connect-gateway, describe-direct-connect-gateways, update-direct-connect-gateway, create-direct-connect-gateway-association, delete-direct-connect-gateway-association, describe-direct-connect-gateway-associations, update-direct-connect-gateway-association, describe-direct-connect-gateway-attachments, create-direct-connect-gateway-association-proposal, delete-direct-connect-gateway-association-proposal, accept-direct-connect-gateway-association-proposal, describe-direct-connect-gateway-association-proposals, describe-virtual-gateways |
| Virtual Interfaces | [`virtual-interfaces.md`](virtual-interfaces.md) | create-private-virtual-interface, create-public-virtual-interface, create-transit-virtual-interface, delete-virtual-interface, describe-virtual-interfaces, update-virtual-interface-attributes, confirm-private-virtual-interface, confirm-public-virtual-interface, confirm-transit-virtual-interface, allocate-private-virtual-interface, allocate-public-virtual-interface, allocate-transit-virtual-interface, associate-virtual-interface, describe-router-configuration |
| LAGs | [`lags.md`](lags.md) | create-lag, delete-lag, describe-lags, update-lag |
| BGP | [`bgp.md`](bgp.md) | create-bgp-peer, delete-bgp-peer, start-bgp-failover-test, stop-bgp-failover-test, list-virtual-interface-test-history |
| MACsec | [`macsec.md`](macsec.md) | associate-mac-sec-key, disassociate-mac-sec-key |
| Interconnects | [`interconnects.md`](interconnects.md) | create-interconnect, delete-interconnect, describe-interconnects |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, describe-tags |
