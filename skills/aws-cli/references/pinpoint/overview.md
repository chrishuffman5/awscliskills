# AWS CLI v2 — Amazon Pinpoint

## Overview

Complete reference for `aws pinpoint` and `aws pinpoint-sms-voice-v2` subcommands in AWS CLI v2. Covers application management, campaigns, journeys, segments, message templates, channels, endpoints, direct messaging, import/export jobs, event streams, recommender configurations, SMS/Voice v2 configuration sets, pools, phone numbers, sender IDs, opt-out lists, protect configurations, registrations, and account settings. Amazon Pinpoint enables targeted customer engagement across push, email, SMS, and voice channels.

## Quick Reference — Common Workflows

### Create an application
```bash
aws pinpoint create-app \
    --create-application-request Name=MyApp
```

### Send a direct SMS message (Pinpoint)
```bash
aws pinpoint send-messages \
    --application-id abc123 \
    --message-request '{
        "Addresses":{"+12065551234":{"ChannelType":"SMS"}},
        "MessageConfiguration":{"SMSMessage":{"Body":"Hello from Pinpoint!","MessageType":"TRANSACTIONAL"}}
    }'
```

### Send a text message (SMS Voice v2)
```bash
aws pinpoint-sms-voice-v2 send-text-message \
    --destination-phone-number +12065551234 \
    --origination-identity +18005551234 \
    --message-body "Hello from SMS Voice v2!" \
    --message-type TRANSACTIONAL
```

### Create a campaign
```bash
aws pinpoint create-campaign \
    --application-id abc123 \
    --write-campaign-request '{
        "Name":"WelcomeCampaign",
        "SegmentId":"seg-123",
        "MessageConfiguration":{"EmailMessage":{"Title":"Welcome!","Body":"Welcome to our service.","FromAddress":"no-reply@example.com"}},
        "Schedule":{"StartTime":"IMMEDIATE","Frequency":"ONCE"}
    }'
```

### Create a segment
```bash
aws pinpoint create-segment \
    --application-id abc123 \
    --write-segment-request '{
        "Name":"ActiveUsers",
        "Dimensions":{"Behavior":{"Recency":{"Duration":"DAY_30","RecencyType":"ACTIVE"}}}
    }'
```

### Request a phone number (SMS Voice v2)
```bash
aws pinpoint-sms-voice-v2 request-phone-number \
    --iso-country-code US \
    --message-type TRANSACTIONAL \
    --number-capabilities SMS VOICE \
    --number-type TOLL_FREE
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Applications | [`apps.md`](apps.md) | `create-app`, `get-app`, `get-apps`, `delete-app`, `update-application-settings`, `get-application-settings`, `get-application-date-range-kpi` |
| Campaigns | [`campaigns.md`](campaigns.md) | `create-campaign`, `get-campaign`, `get-campaigns`, `update-campaign`, `delete-campaign`, `get-campaign-activities`, `get-campaign-date-range-kpi`, `get-campaign-version`, `get-campaign-versions` |
| Journeys | [`journeys.md`](journeys.md) | `create-journey`, `get-journey`, `list-journeys`, `update-journey`, `delete-journey`, `update-journey-state`, `get-journey-date-range-kpi`, `get-journey-execution-metrics`, `get-journey-execution-activity-metrics`, `get-journey-runs`, `get-journey-run-execution-metrics`, `get-journey-run-execution-activity-metrics` |
| Segments | [`segments.md`](segments.md) | `create-segment`, `get-segment`, `get-segments`, `update-segment`, `delete-segment`, `get-segment-version`, `get-segment-versions`, `get-segment-export-jobs`, `get-segment-import-jobs` |
| Templates | [`templates.md`](templates.md) | `create-email-template`, `create-sms-template`, `create-push-template`, `create-voice-template`, `create-in-app-template`, `get-email-template`, `get-sms-template`, `get-push-template`, `get-voice-template`, `get-in-app-template`, `update-email-template`, `update-sms-template`, `update-push-template`, `update-voice-template`, `update-in-app-template`, `delete-email-template`, `delete-sms-template`, `delete-push-template`, `delete-voice-template`, `delete-in-app-template`, `list-templates`, `list-template-versions`, `update-template-active-version` |
| Channels | [`channels.md`](channels.md) | `get-channels`, `get-email-channel`, `update-email-channel`, `delete-email-channel`, `get-sms-channel`, `update-sms-channel`, `delete-sms-channel`, `get-voice-channel`, `update-voice-channel`, `delete-voice-channel`, `get-apns-channel`, `update-apns-channel`, `delete-apns-channel`, `get-gcm-channel`, `update-gcm-channel`, `delete-gcm-channel`, `get-adm-channel`, `update-adm-channel`, `delete-adm-channel`, `get-baidu-channel`, `update-baidu-channel`, `delete-baidu-channel`, `get-apns-sandbox-channel`, `update-apns-sandbox-channel`, `delete-apns-sandbox-channel`, `get-apns-voip-channel`, `update-apns-voip-channel`, `delete-apns-voip-channel`, `get-apns-voip-sandbox-channel`, `update-apns-voip-sandbox-channel`, `delete-apns-voip-sandbox-channel` |
| Endpoints | [`endpoints.md`](endpoints.md) | `get-endpoint`, `update-endpoint`, `delete-endpoint`, `get-user-endpoints`, `delete-user-endpoints`, `update-endpoints-batch` |
| Messaging | [`messaging.md`](messaging.md) | `send-messages`, `send-users-messages`, `send-otp-message`, `verify-otp-message`, `put-events`, `get-in-app-messages` |
| Import & Export | [`import-export.md`](import-export.md) | `create-import-job`, `get-import-job`, `get-import-jobs`, `create-export-job`, `get-export-job`, `get-export-jobs` |
| Event Stream & Recommenders | [`event-stream.md`](event-stream.md) | `put-event-stream`, `get-event-stream`, `delete-event-stream`, `create-recommender-configuration`, `get-recommender-configuration`, `get-recommender-configurations`, `update-recommender-configuration`, `delete-recommender-configuration` |
| Tags & Utilities | [`tags-utilities.md`](tags-utilities.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource`, `phone-number-validate`, `remove-attributes` |
| SMS v2 Configuration Sets | [`sms-configuration-sets.md`](sms-configuration-sets.md) | `create-configuration-set`, `describe-configuration-sets`, `delete-configuration-set`, `create-event-destination`, `update-event-destination`, `delete-event-destination` |
| SMS v2 Pools | [`sms-pools.md`](sms-pools.md) | `create-pool`, `describe-pools`, `update-pool`, `delete-pool`, `list-pool-origination-identities`, `associate-origination-identity`, `disassociate-origination-identity` |
| SMS v2 Phone Numbers | [`sms-phone-numbers.md`](sms-phone-numbers.md) | `request-phone-number`, `describe-phone-numbers`, `update-phone-number`, `release-phone-number`, `create-verified-destination-number`, `describe-verified-destination-numbers`, `delete-verified-destination-number`, `send-destination-number-verification-code`, `verify-destination-number` |
| SMS v2 Sender IDs | [`sms-sender-ids.md`](sms-sender-ids.md) | `request-sender-id`, `describe-sender-ids`, `update-sender-id`, `release-sender-id` |
| SMS v2 Messaging | [`sms-messaging.md`](sms-messaging.md) | `send-text-message`, `send-voice-message`, `send-media-message`, `put-message-feedback` |
| SMS v2 Opt-Out & Keywords | [`sms-opt-out.md`](sms-opt-out.md) | `create-opt-out-list`, `describe-opt-out-lists`, `delete-opt-out-list`, `put-opted-out-number`, `delete-opted-out-number`, `describe-opted-out-numbers`, `put-keyword`, `delete-keyword`, `describe-keywords` |
| SMS v2 Protect Configurations | [`sms-protect.md`](sms-protect.md) | `create-protect-configuration`, `describe-protect-configurations`, `update-protect-configuration`, `delete-protect-configuration`, `associate-protect-configuration`, `disassociate-protect-configuration`, `set-account-default-protect-configuration`, `delete-account-default-protect-configuration`, `get-protect-configuration-country-rule-set`, `update-protect-configuration-country-rule-set`, `put-protect-configuration-rule-set-number-override`, `delete-protect-configuration-rule-set-number-override`, `list-protect-configuration-rule-set-number-overrides` |
| SMS v2 Registrations | [`sms-registrations.md`](sms-registrations.md) | `create-registration`, `describe-registrations`, `delete-registration`, `create-registration-version`, `describe-registration-versions`, `submit-registration-version`, `discard-registration-version`, `create-registration-association`, `list-registration-associations`, `create-registration-attachment`, `describe-registration-attachments`, `delete-registration-attachment`, `put-registration-field-value`, `delete-registration-field-value`, `describe-registration-field-values`, `describe-registration-field-definitions`, `describe-registration-section-definitions`, `describe-registration-type-definitions` |
| SMS v2 Account & Settings | [`sms-account.md`](sms-account.md) | `describe-account-attributes`, `describe-account-limits`, `describe-spend-limits`, `set-text-message-spend-limit-override`, `delete-text-message-spend-limit-override`, `set-voice-message-spend-limit-override`, `delete-voice-message-spend-limit-override`, `set-media-message-spend-limit-override`, `delete-media-message-spend-limit-override`, `set-default-message-type`, `delete-default-message-type`, `set-default-sender-id`, `delete-default-sender-id`, `set-default-message-feedback-enabled`, `carrier-lookup`, `tag-resource`, `untag-resource`, `list-tags-for-resource`, `put-resource-policy`, `get-resource-policy`, `delete-resource-policy` |
