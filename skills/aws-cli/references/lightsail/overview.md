# AWS CLI v2 — Lightsail

## Overview

Complete reference for all `aws lightsail` subcommands in AWS CLI v2. Covers instance management, disks and snapshots, load balancers, managed databases, container services, CDN distributions, domains and DNS, object storage buckets, SSL/TLS certificates, networking, key pairs, alarms, and contact methods.

## Quick Reference — Common Workflows

### Create an instance
```bash
aws lightsail create-instances --instance-names my-instance \
  --availability-zone us-east-1a \
  --blueprint-id amazon_linux_2 \
  --bundle-id micro_3_0
```

### Create a static IP and attach to instance
```bash
aws lightsail allocate-static-ip --static-ip-name my-static-ip
aws lightsail attach-static-ip --static-ip-name my-static-ip \
  --instance-name my-instance
```

### Create a disk and attach
```bash
aws lightsail create-disk --disk-name my-disk \
  --availability-zone us-east-1a --size-in-gb 32
aws lightsail attach-disk --disk-name my-disk \
  --instance-name my-instance --disk-path /dev/xvdf
```

### Create a load balancer with TLS
```bash
aws lightsail create-load-balancer --load-balancer-name my-lb \
  --instance-port 80 \
  --certificate-name my-cert \
  --certificate-domain-name example.com
```

### Create a managed database
```bash
aws lightsail create-relational-database \
  --relational-database-name my-db \
  --relational-database-blueprint-id mysql_8_0 \
  --relational-database-bundle-id micro_2_0 \
  --master-database-name mydb \
  --master-username admin
```

### Create a container service and deploy
```bash
aws lightsail create-container-service --service-name my-container \
  --power micro --scale 1
aws lightsail create-container-service-deployment \
  --service-name my-container \
  --containers '{"webapp":{"image":"nginx:latest","ports":{"80":"HTTP"}}}' \
  --public-endpoint '{"containerName":"webapp","containerPort":80}'
```

### Create a snapshot
```bash
aws lightsail create-instance-snapshot --instance-name my-instance \
  --instance-snapshot-name my-snapshot
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Instances | [`instances.md`](instances.md) | create-instances, create-instances-from-snapshot, delete-instance, get-instance, get-instances, get-instance-state, get-instance-access-details, get-instance-metric-data, get-instance-port-states, reboot-instance, start-instance, stop-instance, update-instance-metadata-options, open-instance-public-ports, close-instance-public-ports, put-instance-public-ports, set-ip-address-type, get-blueprints, get-bundles, get-regions |
| Instance Snapshots | [`instance-snapshots.md`](instance-snapshots.md) | create-instance-snapshot, delete-instance-snapshot, get-instance-snapshot, get-instance-snapshots, copy-snapshot, export-snapshot, get-export-snapshot-records, create-cloud-formation-stack, get-cloud-formation-stack-records |
| Disks | [`disks.md`](disks.md) | create-disk, create-disk-from-snapshot, delete-disk, get-disk, get-disks, attach-disk, detach-disk, create-disk-snapshot, delete-disk-snapshot, get-disk-snapshot, get-disk-snapshots, get-auto-snapshots, delete-auto-snapshot, enable-add-on, disable-add-on |
| Load Balancers | [`load-balancers.md`](load-balancers.md) | create-load-balancer, delete-load-balancer, get-load-balancer, get-load-balancers, get-load-balancer-metric-data, get-load-balancer-tls-certificates, get-load-balancer-tls-policies, attach-instances-to-load-balancer, detach-instances-from-load-balancer, create-load-balancer-tls-certificate, delete-load-balancer-tls-certificate, attach-load-balancer-tls-certificate, update-load-balancer-attribute |
| Databases | [`databases.md`](databases.md) | create-relational-database, create-relational-database-from-snapshot, delete-relational-database, get-relational-database, get-relational-databases, reboot-relational-database, start-relational-database, stop-relational-database, update-relational-database, update-relational-database-parameters, get-relational-database-parameters, get-relational-database-master-user-password, get-relational-database-metric-data, get-relational-database-events, get-relational-database-log-events, get-relational-database-log-streams, get-relational-database-blueprints, get-relational-database-bundles, create-relational-database-snapshot, delete-relational-database-snapshot, get-relational-database-snapshot, get-relational-database-snapshots |
| Containers | [`containers.md`](containers.md) | create-container-service, delete-container-service, get-container-services, update-container-service, create-container-service-deployment, get-container-service-deployments, get-container-service-metric-data, get-container-service-powers, get-container-images, delete-container-image, register-container-image, get-container-log |
| Distributions | [`distributions.md`](distributions.md) | create-distribution, delete-distribution, get-distributions, update-distribution, update-distribution-bundle, get-distribution-bundles, get-distribution-latest-cache-reset, get-distribution-metric-data, reset-distribution-cache, attach-certificate-to-distribution, detach-certificate-from-distribution |
| Domains | [`domains.md`](domains.md) | create-domain, delete-domain, get-domain, get-domains, create-domain-entry, update-domain-entry, delete-domain-entry |
| Buckets | [`buckets.md`](buckets.md) | create-bucket, delete-bucket, get-buckets, update-bucket, update-bucket-bundle, get-bucket-bundles, get-bucket-access-keys, create-bucket-access-key, delete-bucket-access-key, get-bucket-metric-data, set-resource-access-for-bucket |
| Certificates | [`certificates.md`](certificates.md) | create-certificate, delete-certificate, get-certificates |
| Networking | [`networking.md`](networking.md) | allocate-static-ip, release-static-ip, get-static-ip, get-static-ips, attach-static-ip, detach-static-ip, is-vpc-peered, peer-vpc, unpeer-vpc |
| Key Pairs | [`key-pairs.md`](key-pairs.md) | create-key-pair, delete-key-pair, get-key-pair, get-key-pairs, import-key-pair, download-default-key-pair, delete-known-host-keys |
| Alarms | [`alarms.md`](alarms.md) | put-alarm, delete-alarm, get-alarms, test-alarm |
| Contacts & Tags | [`contacts-tags.md`](contacts-tags.md) | create-contact-method, delete-contact-method, get-contact-methods, send-contact-method-verification, tag-resource, untag-resource, get-cost-estimate, get-active-names, get-operation, get-operations, get-operations-for-resource |
