# AWS CLI v2 — CloudWatch RUM

## Overview

Complete reference for all `aws rum` subcommands in AWS CLI v2. Covers application monitor management, real-user monitoring data retrieval, custom metric definitions, metrics destinations, resource policies, event ingestion, and tagging. CloudWatch RUM (Real-User Monitoring) collects real-time data about how users interact with your web applications, providing insights into performance, errors, and user behavior through client-side telemetry.

## Quick Reference — Common Workflows

### Create an app monitor for a web application
```bash
aws rum create-app-monitor \
    --name my-web-app \
    --domain example.com \
    --app-monitor-configuration '{
        "IdentityPoolId":"us-east-1:12345678-1234-1234-1234-123456789012",
        "SessionSampleRate":0.1,
        "Telemetries":["errors","performance","http"],
        "AllowCookies":true,
        "EnableXRay":true
    }' \
    --cw-log-enabled
```

### Send metrics to CloudWatch with custom dimensions
```bash
aws rum put-rum-metrics-destination \
    --app-monitor-name my-web-app \
    --destination CloudWatch

aws rum batch-create-rum-metric-definitions \
    --app-monitor-name my-web-app \
    --destination CloudWatch \
    --metric-definitions '[{
        "Name":"PerformanceNavigationDuration",
        "ValueKey":"event_details.duration",
        "EventPattern":"{\"event_type\":[\"com.amazon.rum.performance_navigation_event\"]}",
        "DimensionKeys":{"metadata.browserName":"BrowserName","metadata.countryCode":"CountryCode"}
    }]'
```

### Query app monitor data
```bash
aws rum get-app-monitor-data \
    --name my-web-app \
    --time-range After=1700000000 \
    --filters Name=EventType,Values=com.amazon.rum.js_error_event
```

### Set up resource policy for cross-account access
```bash
aws rum put-resource-policy \
    --name my-web-app \
    --policy-document '{"Version":"2012-10-17","Statement":[{"Effect":"Allow","Principal":{"AWS":"arn:aws:iam::987654321098:root"},"Action":"rum:PutRumEvents","Resource":"arn:aws:rum:us-east-1:123456789012:appmonitor/my-web-app"}]}'
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| App Monitors | [app-monitors.md](app-monitors.md) | `create-app-monitor`, `get-app-monitor`, `list-app-monitors`, `update-app-monitor`, `delete-app-monitor`, `get-app-monitor-data`, `put-rum-events` |
| Metrics | [metrics.md](metrics.md) | `batch-create-rum-metric-definitions`, `batch-delete-rum-metric-definitions`, `batch-get-rum-metric-definitions`, `update-rum-metric-definition`, `put-rum-metrics-destination`, `list-rum-metrics-destinations`, `delete-rum-metrics-destination` |
| Resource Policies & Tags | [resource-policies-tags.md](resource-policies-tags.md) | `put-resource-policy`, `get-resource-policy`, `delete-resource-policy`, `tag-resource`, `untag-resource`, `list-tags-for-resource` |
