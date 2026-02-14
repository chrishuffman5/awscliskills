# AWS CLI v2 — Amazon Chime SDK

## Overview

Complete reference for all `aws chime-sdk-identity`, `aws chime-sdk-meetings`, `aws chime-sdk-messaging`, and `aws chime-sdk-voice` subcommands in AWS CLI v2. The Amazon Chime SDK enables developers to add real-time voice, video, messaging, and screen sharing capabilities to their applications. This merged reference covers identity management (app instances, users, bots), meetings and attendees, messaging channels, and voice connectivity (voice connectors, SIP media applications, phone numbers, proxy sessions, and voice profiles).

## Quick Reference — Common Workflows

### Set up an app instance with user (Identity)
```bash
aws chime-sdk-identity create-app-instance \
    --name "my-chat-app"

aws chime-sdk-identity create-app-instance-user \
    --app-instance-arn arn:aws:chime:us-east-1:123456789012:app-instance/abc123 \
    --app-instance-user-id user-001 \
    --name "Alice"

aws chime-sdk-identity create-app-instance-admin \
    --app-instance-arn arn:aws:chime:us-east-1:123456789012:app-instance/abc123 \
    --app-instance-admin-arn arn:aws:chime:us-east-1:123456789012:app-instance/abc123/user/user-001
```

### Create a meeting with attendees (Meetings)
```bash
aws chime-sdk-meetings create-meeting \
    --media-region us-east-1 \
    --external-meeting-id "standup-2026-02-13" \
    --meeting-features '{"Audio":{"EchoReduction":"AVAILABLE"},"Video":{"MaxResolution":"HD"},"Attendee":{"MaxCount":25}}'

aws chime-sdk-meetings create-attendee \
    --meeting-id a]1b2c3d4-5678-90ab-cdef-EXAMPLE11111 \
    --external-user-id user-001
```

### Create a messaging channel (Messaging)
```bash
aws chime-sdk-messaging create-channel \
    --app-instance-arn arn:aws:chime:us-east-1:123456789012:app-instance/abc123 \
    --name "general" \
    --mode UNRESTRICTED \
    --privacy PUBLIC \
    --chime-bearer arn:aws:chime:us-east-1:123456789012:app-instance/abc123/user/user-001

aws chime-sdk-messaging send-channel-message \
    --channel-arn arn:aws:chime:us-east-1:123456789012:app-instance/abc123/channel/general \
    --content "Hello team!" \
    --type STANDARD \
    --persistence PERSISTENT \
    --chime-bearer arn:aws:chime:us-east-1:123456789012:app-instance/abc123/user/user-001
```

### Set up voice connectivity (Voice)
```bash
aws chime-sdk-voice create-voice-connector \
    --name my-connector \
    --require-encryption \
    --aws-region us-east-1

aws chime-sdk-voice put-voice-connector-origination \
    --voice-connector-id abc123 \
    --origination '{"Routes":[{"Host":"10.0.0.1","Port":5060,"Protocol":"TCP","Priority":1,"Weight":1}]}'

aws chime-sdk-voice put-voice-connector-termination \
    --voice-connector-id abc123 \
    --termination '{"CallingRegions":["US"],"CidrAllowedList":["10.0.0.0/24"],"CpsLimit":1}'
```

## Command Reference

| Group | File | Commands (CLI Namespace) |
|-------|------|--------------------------|
| App Instances | [app-instances.md](app-instances.md) | `create-app-instance`, `describe-app-instance`, `list-app-instances`, `update-app-instance`, `delete-app-instance`, `get-app-instance-retention-settings`, `put-app-instance-retention-settings` (chime-sdk-identity) |
| App Instance Users | [app-instance-users.md](app-instance-users.md) | `create-app-instance-user`, `describe-app-instance-user`, `list-app-instance-users`, `update-app-instance-user`, `delete-app-instance-user`, `register-app-instance-user-endpoint`, `describe-app-instance-user-endpoint`, `list-app-instance-user-endpoints`, `deregister-app-instance-user-endpoint`, `update-app-instance-user-endpoint`, `put-app-instance-user-expiration-settings` (chime-sdk-identity) |
| App Instance Admins & Bots | [app-instance-admins-bots.md](app-instance-admins-bots.md) | `create-app-instance-admin`, `describe-app-instance-admin`, `list-app-instance-admins`, `delete-app-instance-admin`, `create-app-instance-bot`, `describe-app-instance-bot`, `list-app-instance-bots`, `update-app-instance-bot`, `delete-app-instance-bot` (chime-sdk-identity) |
| Meetings | [meetings.md](meetings.md) | `create-meeting`, `create-meeting-with-attendees`, `get-meeting`, `list-attendees`, `delete-meeting`, `start-meeting-transcription`, `stop-meeting-transcription` (chime-sdk-meetings) |
| Attendees | [attendees.md](attendees.md) | `create-attendee`, `batch-create-attendee`, `get-attendee`, `delete-attendee`, `update-attendee-capabilities`, `batch-update-attendee-capabilities-except` (chime-sdk-meetings) |
| Channels | [channels.md](channels.md) | `create-channel`, `describe-channel`, `list-channels`, `update-channel`, `delete-channel`, `search-channels`, `list-sub-channels`, `put-channel-expiration-settings` (chime-sdk-messaging) |
| Channel Members & Moderators | [channel-members.md](channel-members.md) | `create-channel-membership`, `batch-create-channel-membership`, `describe-channel-membership`, `list-channel-memberships`, `delete-channel-membership`, `list-channel-memberships-for-app-instance-user`, `describe-channel-membership-for-app-instance-user`, `get-channel-membership-preferences`, `put-channel-membership-preferences`, `create-channel-moderator`, `describe-channel-moderator`, `list-channel-moderators`, `delete-channel-moderator`, `describe-channel-moderated-by-app-instance-user`, `list-channels-moderated-by-app-instance-user`, `create-channel-ban`, `describe-channel-ban`, `list-channel-bans`, `delete-channel-ban` (chime-sdk-messaging) |
| Channel Messages | [channel-messages.md](channel-messages.md) | `send-channel-message`, `get-channel-message`, `list-channel-messages`, `update-channel-message`, `delete-channel-message`, `redact-channel-message`, `get-channel-message-status`, `update-channel-read-marker` (chime-sdk-messaging) |
| Channel Flows | [channel-flows.md](channel-flows.md) | `create-channel-flow`, `describe-channel-flow`, `list-channel-flows`, `update-channel-flow`, `delete-channel-flow`, `associate-channel-flow`, `disassociate-channel-flow`, `list-channels-associated-with-channel-flow`, `channel-flow-callback` (chime-sdk-messaging) |
| Messaging Configuration | [messaging-config.md](messaging-config.md) | `get-messaging-session-endpoint`, `get-messaging-streaming-configurations`, `put-messaging-streaming-configurations`, `delete-messaging-streaming-configurations` (chime-sdk-messaging) |
| Voice Connectors | [voice-connectors.md](voice-connectors.md) | `create-voice-connector`, `get-voice-connector`, `list-voice-connectors`, `update-voice-connector`, `delete-voice-connector`, `create-voice-connector-group`, `get-voice-connector-group`, `list-voice-connector-groups`, `update-voice-connector-group`, `delete-voice-connector-group`, `list-available-voice-connector-regions` (chime-sdk-voice) |
| Voice Connector Configuration | [voice-connector-config.md](voice-connector-config.md) | `put-voice-connector-origination`, `get-voice-connector-origination`, `delete-voice-connector-origination`, `put-voice-connector-termination`, `get-voice-connector-termination`, `delete-voice-connector-termination`, `get-voice-connector-termination-health`, `put-voice-connector-termination-credentials`, `list-voice-connector-termination-credentials`, `delete-voice-connector-termination-credentials`, `put-voice-connector-streaming-configuration`, `get-voice-connector-streaming-configuration`, `delete-voice-connector-streaming-configuration`, `put-voice-connector-logging-configuration`, `get-voice-connector-logging-configuration`, `put-voice-connector-proxy`, `get-voice-connector-proxy`, `delete-voice-connector-proxy`, `put-voice-connector-emergency-calling-configuration`, `get-voice-connector-emergency-calling-configuration`, `delete-voice-connector-emergency-calling-configuration`, `put-voice-connector-external-systems-configuration`, `get-voice-connector-external-systems-configuration`, `delete-voice-connector-external-systems-configuration` (chime-sdk-voice) |
| Phone Numbers | [phone-numbers.md](phone-numbers.md) | `create-phone-number-order`, `get-phone-number-order`, `list-phone-number-orders`, `get-phone-number`, `list-phone-numbers`, `update-phone-number`, `delete-phone-number`, `batch-delete-phone-number`, `batch-update-phone-number`, `restore-phone-number`, `search-available-phone-numbers`, `list-supported-phone-number-countries`, `get-phone-number-settings`, `update-phone-number-settings`, `associate-phone-numbers-with-voice-connector`, `disassociate-phone-numbers-from-voice-connector`, `associate-phone-numbers-with-voice-connector-group`, `disassociate-phone-numbers-from-voice-connector-group` (chime-sdk-voice) |
| SIP Media Applications & Rules | [sip.md](sip.md) | `create-sip-media-application`, `get-sip-media-application`, `list-sip-media-applications`, `update-sip-media-application`, `delete-sip-media-application`, `create-sip-media-application-call`, `update-sip-media-application-call`, `get-sip-media-application-logging-configuration`, `put-sip-media-application-logging-configuration`, `create-sip-rule`, `get-sip-rule`, `list-sip-rules`, `update-sip-rule`, `delete-sip-rule` (chime-sdk-voice) |
| Proxy Sessions | [proxy-sessions.md](proxy-sessions.md) | `create-proxy-session`, `get-proxy-session`, `list-proxy-sessions`, `update-proxy-session`, `delete-proxy-session` (chime-sdk-voice) |
| Voice Profiles | [voice-profiles.md](voice-profiles.md) | `create-voice-profile`, `get-voice-profile`, `list-voice-profiles`, `update-voice-profile`, `delete-voice-profile`, `create-voice-profile-domain`, `get-voice-profile-domain`, `list-voice-profile-domains`, `update-voice-profile-domain`, `delete-voice-profile-domain`, `start-speaker-search-task`, `get-speaker-search-task`, `stop-speaker-search-task`, `start-voice-tone-analysis-task`, `get-voice-tone-analysis-task`, `stop-voice-tone-analysis-task` (chime-sdk-voice) |
| Voice Settings | [voice-settings.md](voice-settings.md) | `get-global-settings`, `update-global-settings`, `validate-e911-address` (chime-sdk-voice) |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` (all namespaces) |
