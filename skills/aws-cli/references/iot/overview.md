# AWS CLI v2 — IoT Core

## Overview

Complete reference for `aws iot`, `aws iot-data`, and `aws iot-jobs-data` subcommands in AWS CLI v2. This merged reference covers the entire AWS IoT Core platform: thing registry management, X.509 certificate and policy management, topic rules, device shadows, jobs and command execution, Device Defender security and audit, fleet indexing, fleet provisioning, OTA updates, software package management, billing groups, data plane operations (publish, shadows, retained messages), and device-side job execution. IoT Core is the foundational service for connecting and managing IoT devices at scale.

## Quick Reference — Common Workflows

### Register a thing with certificate and policy
```bash
# Create a thing type and thing
aws iot create-thing-type --thing-type-name TemperatureSensor
aws iot create-thing --thing-name sensor-001 --thing-type-name TemperatureSensor

# Create keys and certificate
aws iot create-keys-and-certificate --set-as-active \
    --certificate-pem-outfile cert.pem \
    --public-key-outfile public.key \
    --private-key-outfile private.key

# Create and attach policy
aws iot create-policy --policy-name SensorPolicy \
    --policy-document file://policy.json

aws iot attach-policy --policy-name SensorPolicy \
    --target arn:aws:iot:us-east-1:123456789012:cert/abc123

aws iot attach-thing-principal --thing-name sensor-001 \
    --principal arn:aws:iot:us-east-1:123456789012:cert/abc123
```

### Create a topic rule to route messages
```bash
aws iot create-topic-rule --rule-name SensorDataToS3 \
    --topic-rule-payload file://rule.json
```

### Publish and manage device shadows
```bash
# Publish a message
aws iot-data publish --topic "sensors/temperature" \
    --payload '{"temp":72.5}' --qos 1

# Update device shadow
aws iot-data update-thing-shadow --thing-name sensor-001 \
    --payload '{"state":{"desired":{"interval":30}}}' output.json

# Get device shadow
aws iot-data get-thing-shadow --thing-name sensor-001 output.json
```

### Create and deploy a job
```bash
aws iot create-job --job-id firmware-update-001 \
    --targets arn:aws:iot:us-east-1:123456789012:thinggroup/AllSensors \
    --document file://job-document.json \
    --target-selection SNAPSHOT

# Device-side: get and update job execution
aws iot-jobs-data describe-job-execution \
    --job-id firmware-update-001 --thing-name sensor-001 \
    --endpoint-url https://data.jobs.iot.us-east-1.amazonaws.com
```

### Set up Device Defender audit
```bash
aws iot update-account-audit-configuration \
    --audit-check-configurations '{"DEVICE_CERTIFICATE_EXPIRING_CHECK":{"enabled":true}}'

aws iot create-scheduled-audit \
    --scheduled-audit-name DailyAudit \
    --frequency DAILY \
    --target-check-names DEVICE_CERTIFICATE_EXPIRING_CHECK CA_CERTIFICATE_EXPIRING_CHECK
```

### Fleet indexing and search
```bash
aws iot update-indexing-configuration \
    --thing-indexing-configuration thingIndexingMode=REGISTRY_AND_SHADOW

aws iot search-index --query-string "thingTypeName:TemperatureSensor"
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Things | [things.md](things.md) | `create-thing`, `describe-thing`, `list-things`, `update-thing`, `delete-thing`, `create-thing-type`, `describe-thing-type`, `list-thing-types`, `update-thing-type`, `delete-thing-type`, `deprecate-thing-type`, `create-thing-group`, `describe-thing-group`, `list-thing-groups`, `update-thing-group`, `delete-thing-group`, `create-dynamic-thing-group`, `update-dynamic-thing-group`, `delete-dynamic-thing-group`, `add-thing-to-thing-group`, `remove-thing-from-thing-group`, `list-things-in-thing-group`, `list-thing-groups-for-thing`, `list-thing-principals`, `list-thing-principals-v2`, `list-principal-things`, `list-principal-things-v2`, `attach-thing-principal`, `detach-thing-principal`, `list-thing-registration-tasks`, `list-thing-registration-task-reports`, `describe-thing-registration-task`, `start-thing-registration-task`, `stop-thing-registration-task`, `register-thing`, `update-thing-groups-for-thing`, `get-thing-connectivity-data` |
| Certificates | [certificates.md](certificates.md) | `create-keys-and-certificate`, `create-certificate-from-csr`, `describe-certificate`, `list-certificates`, `update-certificate`, `delete-certificate`, `register-certificate`, `register-certificate-without-ca`, `register-ca-certificate`, `describe-ca-certificate`, `list-ca-certificates`, `update-ca-certificate`, `delete-ca-certificate`, `list-certificates-by-ca`, `list-outgoing-certificates`, `transfer-certificate`, `accept-certificate-transfer`, `reject-certificate-transfer`, `cancel-certificate-transfer`, `get-registration-code`, `delete-registration-code`, `create-certificate-provider`, `describe-certificate-provider`, `list-certificate-providers`, `update-certificate-provider`, `delete-certificate-provider` |
| Policies | [policies.md](policies.md) | `create-policy`, `get-policy`, `list-policies`, `delete-policy`, `create-policy-version`, `get-policy-version`, `list-policy-versions`, `delete-policy-version`, `set-default-policy-version`, `attach-policy`, `detach-policy`, `list-attached-policies`, `list-targets-for-policy`, `get-effective-policies`, `test-authorization` |
| Rules | [rules.md](rules.md) | `create-topic-rule`, `get-topic-rule`, `list-topic-rules`, `replace-topic-rule`, `delete-topic-rule`, `enable-topic-rule`, `disable-topic-rule`, `create-topic-rule-destination`, `get-topic-rule-destination`, `list-topic-rule-destinations`, `update-topic-rule-destination`, `delete-topic-rule-destination`, `confirm-topic-rule-destination` |
| Shadows | [shadows.md](shadows.md) | `get-thing-shadow` (iot-data), `update-thing-shadow` (iot-data), `delete-thing-shadow` (iot-data), `list-named-shadows-for-thing` (iot-data) |
| Jobs | [jobs.md](jobs.md) | `create-job`, `describe-job`, `list-jobs`, `update-job`, `cancel-job`, `delete-job`, `get-job-document`, `create-job-template`, `describe-job-template`, `list-job-templates`, `delete-job-template`, `describe-managed-job-template`, `list-managed-job-templates`, `describe-job-execution`, `list-job-executions-for-job`, `list-job-executions-for-thing`, `cancel-job-execution`, `delete-job-execution`, `associate-targets-with-job` |
| Commands | [commands.md](commands.md) | `create-command`, `get-command`, `list-commands`, `update-command`, `delete-command`, `get-command-execution`, `list-command-executions`, `delete-command-execution`, `start-command-execution` (iot-jobs-data) |
| Security | [security.md](security.md) | `create-authorizer`, `describe-authorizer`, `list-authorizers`, `update-authorizer`, `delete-authorizer`, `set-default-authorizer`, `clear-default-authorizer`, `describe-default-authorizer`, `test-invoke-authorizer`, `create-domain-configuration`, `describe-domain-configuration`, `list-domain-configurations`, `update-domain-configuration`, `delete-domain-configuration`, `create-role-alias`, `describe-role-alias`, `list-role-aliases`, `update-role-alias`, `delete-role-alias`, `describe-endpoint`, `describe-event-configurations`, `update-event-configurations`, `describe-encryption-configuration`, `update-encryption-configuration` |
| Audit | [audit.md](audit.md) | `describe-account-audit-configuration`, `update-account-audit-configuration`, `delete-account-audit-configuration`, `create-scheduled-audit`, `describe-scheduled-audit`, `list-scheduled-audits`, `update-scheduled-audit`, `delete-scheduled-audit`, `start-on-demand-audit-task`, `describe-audit-task`, `list-audit-tasks`, `describe-audit-finding`, `list-audit-findings`, `list-related-resources-for-audit-finding`, `create-audit-suppression`, `describe-audit-suppression`, `list-audit-suppressions`, `update-audit-suppression`, `delete-audit-suppression`, `create-mitigation-action`, `describe-mitigation-action`, `list-mitigation-actions`, `update-mitigation-action`, `delete-mitigation-action`, `start-audit-mitigation-actions-task`, `describe-audit-mitigation-actions-task`, `list-audit-mitigation-actions-tasks`, `list-audit-mitigation-actions-executions`, `cancel-audit-mitigation-actions-task` |
| Detect | [detect.md](detect.md) | `create-security-profile`, `describe-security-profile`, `list-security-profiles`, `update-security-profile`, `delete-security-profile`, `attach-security-profile`, `detach-security-profile`, `list-security-profiles-for-target`, `list-targets-for-security-profile`, `create-custom-metric`, `describe-custom-metric`, `list-custom-metrics`, `update-custom-metric`, `delete-custom-metric`, `create-dimension`, `describe-dimension`, `list-dimensions`, `update-dimension`, `delete-dimension`, `list-active-violations`, `list-violation-events`, `put-verification-state-on-violation`, `get-behavior-model-training-summaries`, `start-detect-mitigation-actions-task`, `describe-detect-mitigation-actions-task`, `list-detect-mitigation-actions-tasks`, `list-detect-mitigation-actions-executions`, `cancel-detect-mitigation-actions-task`, `list-metric-values`, `validate-security-profile-behaviors` |
| Fleet Indexing | [fleet-indexing.md](fleet-indexing.md) | `get-indexing-configuration`, `update-indexing-configuration`, `describe-index`, `list-indices`, `search-index`, `get-statistics`, `get-cardinality`, `get-percentiles`, `get-buckets-aggregation`, `create-fleet-metric`, `describe-fleet-metric`, `list-fleet-metrics`, `update-fleet-metric`, `delete-fleet-metric` |
| Provisioning | [provisioning.md](provisioning.md) | `create-provisioning-template`, `describe-provisioning-template`, `list-provisioning-templates`, `update-provisioning-template`, `delete-provisioning-template`, `create-provisioning-template-version`, `describe-provisioning-template-version`, `list-provisioning-template-versions`, `delete-provisioning-template-version`, `create-provisioning-claim` |
| OTA Updates | [ota-updates.md](ota-updates.md) | `create-ota-update`, `get-ota-update`, `list-ota-updates`, `delete-ota-update`, `create-stream`, `describe-stream`, `list-streams`, `update-stream`, `delete-stream` |
| Packages | [packages.md](packages.md) | `create-package`, `get-package`, `list-packages`, `update-package`, `delete-package`, `get-package-configuration`, `update-package-configuration`, `create-package-version`, `get-package-version`, `list-package-versions`, `update-package-version`, `delete-package-version`, `associate-sbom-with-package-version`, `disassociate-sbom-from-package-version`, `list-sbom-validation-results` |
| Billing Groups | [billing-groups.md](billing-groups.md) | `create-billing-group`, `describe-billing-group`, `list-billing-groups`, `update-billing-group`, `delete-billing-group`, `add-thing-to-billing-group`, `remove-thing-from-billing-group`, `list-things-in-billing-group` |
| Data Plane | [data-plane.md](data-plane.md) | `publish` (iot-data), `get-retained-message` (iot-data), `list-retained-messages` (iot-data), `delete-connection` (iot-data), `describe-job-execution` (iot-jobs-data), `get-pending-job-executions` (iot-jobs-data), `start-next-pending-job-execution` (iot-jobs-data), `update-job-execution` (iot-jobs-data) |
| Logging | [logging.md](logging.md) | `get-logging-options`, `set-logging-options`, `get-v2-logging-options`, `set-v2-logging-options`, `list-v2-logging-levels`, `set-v2-logging-level`, `delete-v2-logging-level` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
