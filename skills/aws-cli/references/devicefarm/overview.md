# AWS CLI v2 — Device Farm

## Overview

Complete reference for all `aws devicefarm` subcommands in AWS CLI v2. Covers project management, device pool configuration, test runs, jobs, suites, tests, uploads, remote access sessions, network profiles, instance profiles, VPCE configurations, test grid (Selenium) projects, and device slot offerings.

## Quick Reference — Common Workflows

### Create a project
```bash
aws devicefarm create-project --name my-test-project \
  --default-job-timeout-minutes 60
```

### Create a device pool
```bash
aws devicefarm create-device-pool \
  --project-arn arn:aws:devicefarm:us-west-2:123456789012:project:uuid \
  --name "Android Phones" \
  --rules '[{"attribute":"PLATFORM","operator":"EQUALS","value":"\"ANDROID\""}]'
```

### Upload a test package
```bash
aws devicefarm create-upload \
  --project-arn arn:aws:devicefarm:us-west-2:123456789012:project:uuid \
  --name app.apk --type ANDROID_APP
# Use the returned URL to upload via curl
curl -T app.apk "presigned-url"
```

### Schedule a test run
```bash
aws devicefarm schedule-run \
  --project-arn arn:aws:devicefarm:us-west-2:123456789012:project:uuid \
  --app-arn arn:aws:devicefarm:us-west-2:123456789012:upload:uuid \
  --device-pool-arn arn:aws:devicefarm:us-west-2:123456789012:devicepool:uuid \
  --test type=BUILTIN_FUZZ
```

### Create a remote access session
```bash
aws devicefarm create-remote-access-session \
  --project-arn arn:aws:devicefarm:us-west-2:123456789012:project:uuid \
  --device-arn arn:aws:devicefarm:us-west-2::device:uuid \
  --name "Debug Session"
```

### Create a Selenium test grid project
```bash
aws devicefarm create-test-grid-project \
  --name "Web Tests" \
  --description "Selenium browser testing"
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Projects | [`projects.md`](projects.md) | create-project, delete-project, get-project, list-projects, update-project, get-account-settings |
| Device Pools | [`device-pools.md`](device-pools.md) | create-device-pool, delete-device-pool, get-device-pool, list-device-pools, update-device-pool, get-device-pool-compatibility, get-device, list-devices |
| Runs | [`runs.md`](runs.md) | schedule-run, stop-run, delete-run, get-run, list-runs, list-unique-problems |
| Jobs, Suites & Tests | [`jobs-suites-tests.md`](jobs-suites-tests.md) | get-job, list-jobs, stop-job, get-suite, list-suites, get-test, list-tests, list-samples, list-artifacts |
| Uploads | [`uploads.md`](uploads.md) | create-upload, delete-upload, get-upload, list-uploads, update-upload, install-to-remote-access-session |
| Remote Access | [`remote-access.md`](remote-access.md) | create-remote-access-session, delete-remote-access-session, get-remote-access-session, list-remote-access-sessions, stop-remote-access-session |
| Network Profiles | [`network-profiles.md`](network-profiles.md) | create-network-profile, delete-network-profile, get-network-profile, list-network-profiles, update-network-profile |
| Instance Profiles | [`instance-profiles.md`](instance-profiles.md) | create-instance-profile, delete-instance-profile, get-instance-profile, list-instance-profiles, update-instance-profile |
| VPCE Configurations | [`vpce-configs.md`](vpce-configs.md) | create-vpce-configuration, delete-vpce-configuration, get-vpce-configuration, list-vpce-configurations, update-vpce-configuration |
| Test Grid | [`test-grid.md`](test-grid.md) | create-test-grid-project, delete-test-grid-project, get-test-grid-project, list-test-grid-projects, update-test-grid-project, create-test-grid-url, get-test-grid-session, list-test-grid-sessions, list-test-grid-session-actions, list-test-grid-session-artifacts |
| Offerings | [`offerings.md`](offerings.md) | list-offerings, list-offering-promotions, list-offering-transactions, get-offering-status, purchase-offering, renew-offering |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
