# AWS CLI v2 — App Mesh

## Overview

Complete reference for all `aws appmesh` subcommands in AWS CLI v2. Covers service mesh management, virtual nodes, virtual services, virtual routers, routes, virtual gateways, gateway routes, and resource tagging. App Mesh provides application-level networking with service-to-service communication using the Envoy proxy.

## Quick Reference — Common Workflows

### Create a mesh
```bash
aws appmesh create-mesh --mesh-name my-mesh \
  --spec egressFilter={type=DROP_ALL}
```

### Create a virtual node with DNS service discovery
```bash
aws appmesh create-virtual-node --mesh-name my-mesh \
  --virtual-node-name my-service-v1 \
  --spec '{
    "listeners": [{"portMapping": {"port": 8080, "protocol": "http"}}],
    "serviceDiscovery": {"dns": {"hostname": "my-service.local"}}
  }'
```

### Create a virtual router and route for weighted traffic splitting
```bash
aws appmesh create-virtual-router --mesh-name my-mesh \
  --virtual-router-name my-router \
  --spec 'listeners=[{portMapping={port=8080,protocol=http}}]'

aws appmesh create-route --mesh-name my-mesh \
  --virtual-router-name my-router \
  --route-name my-route \
  --spec '{
    "httpRoute": {
      "match": {"prefix": "/"},
      "action": {
        "weightedTargets": [
          {"virtualNode": "my-service-v1", "weight": 90},
          {"virtualNode": "my-service-v2", "weight": 10}
        ]
      }
    }
  }'
```

### Create a virtual service backed by a virtual router
```bash
aws appmesh create-virtual-service --mesh-name my-mesh \
  --virtual-service-name my-service.local \
  --spec 'provider={virtualRouter={virtualRouterName=my-router}}'
```

### Create a virtual gateway for ingress traffic
```bash
aws appmesh create-virtual-gateway --mesh-name my-mesh \
  --virtual-gateway-name my-gateway \
  --spec 'listeners=[{portMapping={port=9080,protocol=http}}]'

aws appmesh create-gateway-route --mesh-name my-mesh \
  --virtual-gateway-name my-gateway \
  --gateway-route-name my-gw-route \
  --spec '{
    "httpRoute": {
      "match": {"prefix": "/"},
      "action": {"target": {"virtualService": {"virtualServiceName": "my-service.local"}}}
    }
  }'
```

### List all resources in a mesh
```bash
aws appmesh list-virtual-nodes --mesh-name my-mesh --query 'virtualNodes[].virtualNodeName'
aws appmesh list-virtual-services --mesh-name my-mesh --query 'virtualServices[].virtualServiceName'
aws appmesh list-virtual-routers --mesh-name my-mesh --query 'virtualRouters[].virtualRouterName'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Meshes | [`meshes.md`](meshes.md) | create-mesh, delete-mesh, describe-mesh, list-meshes, update-mesh |
| Virtual Nodes | [`virtual-nodes.md`](virtual-nodes.md) | create-virtual-node, delete-virtual-node, describe-virtual-node, list-virtual-nodes, update-virtual-node |
| Virtual Services | [`virtual-services.md`](virtual-services.md) | create-virtual-service, delete-virtual-service, describe-virtual-service, list-virtual-services, update-virtual-service |
| Virtual Routers | [`virtual-routers.md`](virtual-routers.md) | create-virtual-router, delete-virtual-router, describe-virtual-router, list-virtual-routers, update-virtual-router |
| Routes | [`routes.md`](routes.md) | create-route, delete-route, describe-route, list-routes, update-route |
| Virtual Gateways | [`virtual-gateways.md`](virtual-gateways.md) | create-virtual-gateway, delete-virtual-gateway, describe-virtual-gateway, list-virtual-gateways, update-virtual-gateway |
| Gateway Routes | [`gateway-routes.md`](gateway-routes.md) | create-gateway-route, delete-gateway-route, describe-gateway-route, list-gateway-routes, update-gateway-route |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
