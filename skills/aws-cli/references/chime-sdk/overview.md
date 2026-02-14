# AWS CLI v2 — Amazon Chime SDK

## Overview

Complete reference for `aws chime-sdk-identity`, `aws chime-sdk-meetings`, `aws chime-sdk-messaging`, and `aws chime-sdk-voice` subcommands in AWS CLI v2. The Amazon Chime SDK enables developers to add real-time communication capabilities to their applications. The Identity service manages app instances and users. The Meetings service handles audio/video meetings with attendees. The Messaging service provides persistent chat channels. The Voice service manages SIP-based voice connectivity, phone numbers, and voice profiles.

## Quick Reference — Common Workflows

### Create an app instance and user
```bash
aws chime-sdk-identity create-app-instance \
    --name "my-chat-app"

aws chime-sdk-identity create-app-instance-user \
    --app-instance-arn APP_INSTANCE_ARN \
    --app-instance-user-id user001 \
    --name "Jane Doe"
```

### Create a meeting with attendees
```bash
aws chime-sdk-meetings create-meeting \
    --media-region us-east-1 \
    --external-meeting-id "meeting-001" \
    --meeting-features '{"Audio":{"EchoReduction":"AVAILABLE"},"Video":{"MaxResolution":"HD"}}'

aws chime-sdk-meetings create-attendee \
    --meeting-id MEETING_ID \
    --external-user-id "user001"
```

### Create a messaging channel and send a message
```bash
aws chime-sdk-messaging create-channel \
    --app-instance-arn APP_INSTANCE_ARN \
    --name "general-chat" \
    --mode UNRESTRICTED \
    --privacy PUBLIC \
    --chime-bearer APP_INSTANCE_USER_ARN

aws chime-sdk-messaging send-channel-message \
    --channel-arn CHANNEL_ARN \
    --content "Hello, team!" \
    --type STANDARD \
    --persistence PERSISTENT \
    --chime-bearer APP_INSTANCE_USER_ARN
```

### Create a voice connector and manage phone numbers
```bash
aws chime-sdk-voice create-voice-connector \
    --name "my-connector" \
    --require-encryption

aws chime-sdk-voice create-phone-number-order \
    --product-type VoiceConnector \
    --e164-phone-numbers "+12025551234" "+12025555678"

aws chime-sdk-voice associate-phone-numbers-with-voice-connector \
    --voice-connector-id VC_ID \
    --e164-phone-numbers "+12025551234"
```

### Create a SIP media application
```bash
aws chime-sdk-voice create-sip-media-application \
    --aws-region us-east-1 \
    --name "my-sip-app" \
    --endpoints '[{"LambdaArn":"arn:aws:lambda:us-east-1:123456789012:function:sip-handler"}]'
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| App Instances | [app-instances.md](app-instances.md) | `create-app-instance`, `describe-app-instance`, `list-app-instances`, `update-app-instance`, `delete-app-instance`, `get-app-instance-retention-settings`, `put-app-instance-retention-settings` (chime-sdk-identity) |
| App Instance Users | [app-instance-users.md](app-instance-users.md) | `create-app-instance-user`, `describe-app-instance-user`, `list-app-instance-users`, `update-app-instance-user`, `delete-app-instance-user`, `describe-app-instance-user-endpoint`, `list-app-instance-user-endpoints`, `register-app-instance-user-endpoint`, `update-app-instance-user-endpoint`, `deregister-app-instance-user-endpoint`, `put-app-instance-user-expiration-settings` (chime-sdk-identity) |
| App Instance Admin & Bots | [app-instance-admin-bots.md](app-instance-admin-bots.md) | `create-app-instance-admin`, `describe-app-instance-admin`, `list-app-instance-admins`, `delete-app-instance-admin`, `create-app-instance-bot`, `describe-app-instance-bot`, `list-app-instance-bots`, `update-app-instance-bot`, `delete-app-instance-bot` (chime-sdk-identity) |
| Meetings | [meetings.md](meetings.md) | `create-meeting`, `create-meeting-with-attendees`, `get-meeting`, `delete-meeting`, `list-tags-for-resource`, `start-meeting-transcription`, `stop-meeting-transcription` (chime-sdk-meetings) |
| Attendees | [attendees.md](attendees.md) | `create-attendee`, `batch-create-attendee`, `get-attendee`, `list-attendees`, `delete-attendee`, `update-attendee-capabilities`, `batch-update-attendee-capabilities-except` (chime-sdk-meetings) |
| Channels | [channels.md](channels.md) | `create-channel`, `describe-channel`, `list-channels`, `update-channel`, `delete-channel`, `search-channels`, `describe-channel-moderated-by-app-instance-user`, `list-channels-moderated-by-app-instance-user`, `list-sub-channels`, `put-channel-expiration-settings` (chime-sdk-messaging) |
| Channel Memberships | [channel-memberships.md](channel-memberships.md) | `create-channel-membership`, `batch-create-channel-membership`, `describe-channel-membership`, `list-channel-memberships`, `delete-channel-membership`, `describe-channel-membership-for-app-instance-user`, `list-channel-memberships-for-app-instance-user`, `get-channel-membership-preferences`, `put-channel-membership-preferences` (chime-sdk-messaging) |
| Channel Messages | [channel-messages.md](channel-messages.md) | `send-channel-message`, `get-channel-message`, `list-channel-messages`, `update-channel-message`, `delete-channel-message`, `redact-channel-message`, `get-channel-message-status`, `update-channel-read-marker` (chime-sdk-messaging) |
| Channel Flows | [channel-flows.md](channel-flows.md) | `create-channel-flow`, `describe-channel-flow`, `list-channel-flows`, `update-channel-flow`, `delete-channel-flow`, `associate-channel-flow`, `disassociate-channel-flow`, `list-channels-associated-with-channel-flow`, `channel-flow-callback` (chime-sdk-messaging) |
| Channel Moderation | [channel-moderation.md](channel-moderation.md) | `create-channel-ban`, `describe-channel-ban`, `list-channel-bans`, `delete-channel-ban`, `create-channel-moderator`, `describe-channel-moderator`, `list-channel-moderators`, `delete-channel-moderator` (chime-sdk-messaging) |
| Messaging Configuration | [messaging-config.md](messaging-config.md) | `get-messaging-session-endpoint`, `get-messaging-streaming-configurations`, `put-messaging-streaming-configurations`, `delete-messaging-streaming-configurations` (chime-sdk-messaging) |
| Voice Connectors | [voice-connectors.md](voice-connectors.md) | `create-voice-connector`, `get-voice-connector`, `list-voice-connectors`, `update-voice-connector`, `delete-voice-connector`, `create-voice-connector-group`, `get-voice-connector-group`, `list-voice-connector-groups`, `update-voice-connector-group`, `delete-voice-connector-group`, `get-voice-connector-origination`, `put-voice-connector-origination`, `delete-voice-connector-origination`, `get-voice-connector-termination`, `put-voice-connector-termination`, `delete-voice-connector-termination`, `list-voice-connector-termination-credentials`, `put-voice-connector-termination-credentials`, `delete-voice-connector-termination-credentials`, `get-voice-connector-proxy`, `put-voice-connector-proxy`, `delete-voice-connector-proxy`, `get-voice-connector-streaming-configuration`, `put-voice-connector-streaming-configuration`, `delete-voice-connector-streaming-configuration`, `get-voice-connector-logging-configuration`, `put-voice-connector-logging-configuration`, `get-voice-connector-emergency-calling-configuration`, `put-voice-connector-emergency-calling-configuration`, `delete-voice-connector-emergency-calling-configuration`, `get-voice-connector-external-systems-configuration`, `put-voice-connector-external-systems-configuration`, `delete-voice-connector-external-systems-configuration`, `get-voice-connector-termination-health` (chime-sdk-voice) |
| Phone Numbers (Voice) | [phone-numbers-voice.md](phone-numbers-voice.md) | `create-phone-number-order`, `get-phone-number`, `get-phone-number-order`, `list-phone-numbers`, `list-phone-number-orders`, `update-phone-number`, `delete-phone-number`, `batch-delete-phone-number`, `batch-update-phone-number`, `restore-phone-number`, `get-phone-number-settings`, `update-phone-number-settings`, `search-available-phone-numbers`, `list-supported-phone-number-countries`, `associate-phone-numbers-with-voice-connector`, `disassociate-phone-numbers-from-voice-connector`, `associate-phone-numbers-with-voice-connector-group`, `disassociate-phone-numbers-from-voice-connector-group`, `list-available-voice-connector-regions`, `get-global-settings`, `update-global-settings`, `validate-e911-address` (chime-sdk-voice) |
| SIP | [sip.md](sip.md) | `create-sip-media-application`, `get-sip-media-application`, `list-sip-media-applications`, `update-sip-media-application`, `delete-sip-media-application`, `get-sip-media-application-logging-configuration`, `put-sip-media-application-logging-configuration`, `create-sip-media-application-call`, `update-sip-media-application-call`, `create-sip-rule`, `get-sip-rule`, `list-sip-rules`, `update-sip-rule`, `delete-sip-rule` (chime-sdk-voice) |
| Proxy Sessions | [proxy-sessions.md](proxy-sessions.md) | `create-proxy-session`, `get-proxy-session`, `list-proxy-sessions`, `update-proxy-session`, `delete-proxy-session` (chime-sdk-voice) |
| Voice Profiles | [voice-profiles.md](voice-profiles.md) | `create-voice-profile-domain`, `get-voice-profile-domain`, `list-voice-profile-domains`, `update-voice-profile-domain`, `delete-voice-profile-domain`, `create-voice-profile`, `get-voice-profile`, `list-voice-profiles`, `update-voice-profile`, `delete-voice-profile`, `start-speaker-search-task`, `get-speaker-search-task`, `stop-speaker-search-task`, `start-voice-tone-analysis-task`, `get-voice-tone-analysis-task`, `stop-voice-tone-analysis-task` (chime-sdk-voice) |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` (all services) |
