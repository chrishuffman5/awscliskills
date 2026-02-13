# AWS CLI v2 — Cloud Map (Service Discovery)

## Overview

Complete reference for all `aws servicediscovery` subcommands in AWS CLI v2. AWS Cloud Map is a cloud resource discovery service that lets you define custom names for application resources and maintains their locations. Covers namespace management (HTTP, private DNS, public DNS), service definitions, instance registration/discovery, and operations tracking.

## Quick Reference — Common Workflows

### Create a private DNS namespace for ECS
```bash
aws servicediscovery create-private-dns-namespace \
  --name example.local \
  --vpc vpc-1c56417b \
  --description "Private namespace for ECS services"
```

### Create an HTTP namespace
```bash
aws servicediscovery create-http-namespace \
  --name my-http-namespace \
  --description "HTTP-only namespace for API discovery"
```

### Create a service with DNS records
```bash
aws servicediscovery create-service \
  --name my-service \
  --namespace-id ns-abcd1234xmpl5678 \
  --dns-config 'RoutingPolicy=MULTIVALUE,DnsRecords=[{Type=A,TTL=60}]'
```

### Register an instance
```bash
aws servicediscovery register-instance \
  --service-id srv-p5zdwlg5uvvzjita \
  --instance-id i-abcd1234 \
  --attributes AWS_INSTANCE_IPV4=172.2.1.3,AWS_INSTANCE_PORT=8080
```

### Discover instances
```bash
aws servicediscovery discover-instances \
  --namespace-name example.local \
  --service-name my-service \
  --health-status HEALTHY
```

### Check operation status (namespace/instance operations are asynchronous)
```bash
aws servicediscovery get-operation \
  --operation-id gv4g5meo7ndmeh4fqskygvk23d2fijwa-k9302yzd
```

### List all namespaces and services
```bash
aws servicediscovery list-namespaces --query 'Namespaces[].{Name:Name,Type:Type,ID:Id}'
aws servicediscovery list-services --query 'Services[].{Name:Name,ID:Id}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Namespaces | [`namespaces.md`](namespaces.md) | create-http-namespace, create-private-dns-namespace, create-public-dns-namespace, delete-namespace, get-namespace, list-namespaces, update-http-namespace, update-private-dns-namespace, update-public-dns-namespace |
| Services | [`services.md`](services.md) | create-service, delete-service, get-service, list-services, update-service, get-service-attributes, update-service-attributes, delete-service-attributes |
| Instances | [`instances.md`](instances.md) | register-instance, deregister-instance, get-instance, list-instances, get-instances-health-status, update-instance-custom-health-status, discover-instances, discover-instances-revision |
| Operations & Tags | [`operations-tags.md`](operations-tags.md) | get-operation, list-operations, tag-resource, untag-resource, list-tags-for-resource |
