# AWS CLI v2 — WorkSpaces (Virtual Desktops + Web Access)

## Overview

Complete reference for `aws workspaces` and `aws workspaces-web` subcommands in AWS CLI v2. Covers virtual desktop management (create, terminate, reboot, rebuild, start, stop), workspace bundles and images, directory registration, IP access control groups, connection aliases, WorkSpaces pools, account-level settings, and WorkSpaces Web portals (browser settings, network settings, user settings, identity providers, trust stores).

## Quick Reference — Common Workflows

### Create a WorkSpace
```bash
aws workspaces create-workspaces --workspaces \
  DirectoryId=d-1234567890,UserName=jsmith,BundleId=wsb-abcdefghi,\
WorkspaceProperties="{RunningMode=AUTO_STOP,RunningModeAutoStopTimeoutInMinutes=60}"
```

### Describe WorkSpaces
```bash
aws workspaces describe-workspaces --directory-id d-1234567890
```

### Start / Stop WorkSpaces
```bash
aws workspaces start-workspaces --start-workspace-requests WorkspaceId=ws-abc123
aws workspaces stop-workspaces --stop-workspace-requests WorkspaceId=ws-abc123
```

### Reboot a WorkSpace
```bash
aws workspaces reboot-workspaces --reboot-workspace-requests WorkspaceId=ws-abc123
```

### Terminate a WorkSpace
```bash
aws workspaces terminate-workspaces --terminate-workspace-requests WorkspaceId=ws-abc123
```

### Register a directory
```bash
aws workspaces register-workspace-directory \
  --directory-id d-1234567890 \
  --subnet-ids subnet-aaa subnet-bbb \
  --enable-work-docs
```

### Create a WorkSpaces Web portal
```bash
aws workspaces-web create-portal \
  --display-name "My Portal" \
  --additional-encryption-context key1=value1
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| WorkSpaces | [`workspaces.md`](workspaces.md) | create-workspaces, terminate-workspaces, reboot-workspaces, rebuild-workspaces, start-workspaces, stop-workspaces, describe-workspaces, describe-workspaces-connection-status, modify-workspace-properties, modify-workspace-state, restore-workspace, migrate-workspace |
| Bundles & Images | [`bundles-images.md`](bundles-images.md) | create-workspace-bundle, delete-workspace-bundle, describe-workspace-bundles, update-workspace-bundle, create-workspace-image, delete-workspace-image, describe-workspace-images, copy-workspace-image |
| Directories | [`directories.md`](directories.md) | register-workspace-directory, deregister-workspace-directory, describe-workspace-directories, modify-workspace-creation-properties, modify-workspace-access-properties, modify-selfservice-permissions, modify-client-properties, describe-client-properties |
| IP Groups | [`ip-groups.md`](ip-groups.md) | create-ip-group, delete-ip-group, describe-ip-groups, authorize-ip-rules, revoke-ip-rules, update-rules-of-ip-group, associate-ip-groups, disassociate-ip-groups |
| Connection Aliases | [`connection-aliases.md`](connection-aliases.md) | create-connection-alias, delete-connection-alias, describe-connection-aliases, associate-connection-alias, disassociate-connection-alias |
| Pools | [`pools.md`](pools.md) | create-workspaces-pool, terminate-workspaces-pool, describe-workspaces-pools, update-workspaces-pool, start-workspaces-pool, stop-workspaces-pool, describe-workspaces-pool-sessions |
| Account | [`account.md`](account.md) | describe-account, describe-account-modifications, modify-account, create-tags, delete-tags, describe-tags |
| Web Portals | [`web-portals.md`](web-portals.md) | create-portal, delete-portal, get-portal, list-portals, update-portal |
| Web Browser Settings | [`web-browser-settings.md`](web-browser-settings.md) | create-browser-settings, delete-browser-settings, get-browser-settings, list-browser-settings, update-browser-settings, associate-browser-settings, disassociate-browser-settings |
| Web Network Settings | [`web-network-settings.md`](web-network-settings.md) | create-network-settings, delete-network-settings, get-network-settings, list-network-settings, update-network-settings, associate-network-settings, disassociate-network-settings |
| Web User Settings | [`web-user-settings.md`](web-user-settings.md) | create-user-settings, delete-user-settings, get-user-settings, list-user-settings, update-user-settings, associate-user-settings, disassociate-user-settings |
| Web Identity | [`web-identity.md`](web-identity.md) | create-identity-provider, delete-identity-provider, get-identity-provider, list-identity-providers, update-identity-provider |
| Web Trust Stores | [`web-trust-stores.md`](web-trust-stores.md) | create-trust-store, delete-trust-store, get-trust-store, list-trust-stores, update-trust-store, associate-trust-store, disassociate-trust-store |
| Web Tags | [`web-tags.md`](web-tags.md) | tag-resource, untag-resource, list-tags-for-resource |
