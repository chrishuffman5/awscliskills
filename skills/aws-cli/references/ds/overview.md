# AWS CLI v2 — Directory Service

## Overview

Complete reference for all `aws ds` subcommands in AWS CLI v2. AWS Directory Service provides multiple ways to use Microsoft Active Directory (AD) with other AWS services. You can create a Managed Microsoft AD directory, connect to your existing self-managed AD using AD Connector, or create a Simple AD directory. The service supports trust relationships, directory sharing, LDAPS, RADIUS authentication, snapshots, and multi-region replication.

## Quick Reference — Common Workflows

### Create a Managed Microsoft AD
```bash
aws ds create-microsoft-ad --name corp.example.com \
  --password 'MyP@ssw0rd!' \
  --vpc-settings VpcId=vpc-12345678,SubnetIds=subnet-aaaa1111,subnet-bbbb2222 \
  --edition Enterprise
```

### Create an AD Connector
```bash
aws ds connect-directory --name corp.example.com \
  --password 'SvcAcctP@ss' \
  --size Small \
  --connect-settings VpcId=vpc-12345678,SubnetIds=subnet-aaaa1111,subnet-bbbb2222,CustomerDnsIps=10.0.0.10,CustomerUserName=svc_connect
```

### Describe directories
```bash
aws ds describe-directories
aws ds describe-directories --directory-ids d-1234567890
```

### Create a trust relationship
```bash
aws ds create-trust \
  --directory-id d-1234567890 \
  --remote-domain-name remote.example.com \
  --trust-password 'TrustP@ss123' \
  --trust-direction "Two-Way" \
  --trust-type Forest
```

### Share a directory with another account
```bash
aws ds share-directory \
  --directory-id d-1234567890 \
  --share-target Id=987654321098,Type=ACCOUNT \
  --share-method HANDSHAKE \
  --share-notes "Shared directory for dev team"
```

### Enable LDAPS
```bash
aws ds register-certificate --directory-id d-1234567890 \
  --certificate-data file://cert.pem --type ClientLDAPS
aws ds enable-ldaps --directory-id d-1234567890 --type Client
```

### Create and restore from snapshot
```bash
aws ds create-snapshot --directory-id d-1234567890 --name "pre-update-snapshot"
aws ds restore-from-snapshot --snapshot-id s-1234567890
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Directories | [`directories.md`](directories.md) | create-directory, create-microsoft-ad, delete-directory, describe-directories, get-directory-limits, create-alias, create-computer, describe-settings, update-settings, describe-update-directory, update-directory-setup, describe-domain-controllers, update-number-of-domain-controllers, describe-regions, add-region, remove-region |
| Hybrid AD | [`hybrid-ad.md`](hybrid-ad.md) | connect-directory, create-hybrid-ad, describe-hybrid-ad-update, update-hybrid-ad |
| Trusts | [`trusts.md`](trusts.md) | create-trust, delete-trust, describe-trusts, update-trust, verify-trust |
| Conditional Forwarders | [`conditional-forwarders.md`](conditional-forwarders.md) | create-conditional-forwarder, delete-conditional-forwarder, describe-conditional-forwarders, update-conditional-forwarder |
| Snapshots | [`snapshots.md`](snapshots.md) | create-snapshot, delete-snapshot, describe-snapshots, restore-from-snapshot, get-snapshot-limits |
| Networking | [`networking.md`](networking.md) | add-ip-routes, remove-ip-routes, list-ip-routes |
| Authentication | [`authentication.md`](authentication.md) | enable-sso, disable-sso, enable-radius, disable-radius, update-radius, enable-ldaps, disable-ldaps, describe-ldaps-settings, enable-client-authentication, disable-client-authentication, describe-client-authentication-settings, reset-user-password |
| Certificates | [`certificates.md`](certificates.md) | register-certificate, deregister-certificate, describe-certificate, list-certificates, enable-ca-enrollment-policy, disable-ca-enrollment-policy, describe-ca-enrollment-policy |
| Directory Data Access | [`directory-data-access.md`](directory-data-access.md) | enable-directory-data-access, disable-directory-data-access, describe-directory-data-access |
| Sharing | [`sharing.md`](sharing.md) | share-directory, unshare-directory, accept-shared-directory, reject-shared-directory, describe-shared-directories |
| AD Assessments | [`ad-assessments.md`](ad-assessments.md) | start-ad-assessment, delete-ad-assessment, describe-ad-assessment, list-ad-assessments |
| Events & Tags | [`events-tags.md`](events-tags.md) | register-event-topic, deregister-event-topic, describe-event-topics, add-tags-to-resource, remove-tags-from-resource, list-tags-for-resource, create-log-subscription, delete-log-subscription, list-log-subscriptions, start-schema-extension, cancel-schema-extension, list-schema-extensions |
| Wait | [`wait.md`](wait.md) | wait directory-available |
