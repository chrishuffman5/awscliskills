# Amazon Chime SDK — Quick Reference

## Identity Commands (`aws chime-sdk-identity`)

| Command | Description |
|---------|-------------|
| `create-app-instance` | Create an app instance |
| `describe-app-instance` | Describe an app instance |
| `list-app-instances` | List all app instances |
| `update-app-instance` | Update an app instance |
| `delete-app-instance` | Delete an app instance |
| `get-app-instance-retention-settings` | Get retention settings |
| `put-app-instance-retention-settings` | Set retention settings |
| `create-app-instance-user` | Create an app instance user |
| `describe-app-instance-user` | Describe an app instance user |
| `list-app-instance-users` | List app instance users |
| `update-app-instance-user` | Update an app instance user |
| `delete-app-instance-user` | Delete an app instance user |
| `register-app-instance-user-endpoint` | Register a user endpoint |
| `describe-app-instance-user-endpoint` | Describe a user endpoint |
| `list-app-instance-user-endpoints` | List user endpoints |
| `deregister-app-instance-user-endpoint` | Deregister a user endpoint |
| `update-app-instance-user-endpoint` | Update a user endpoint |
| `put-app-instance-user-expiration-settings` | Set user expiration settings |
| `create-app-instance-admin` | Create an app instance admin |
| `describe-app-instance-admin` | Describe an app instance admin |
| `list-app-instance-admins` | List app instance admins |
| `delete-app-instance-admin` | Delete an app instance admin |
| `create-app-instance-bot` | Create an app instance bot |
| `describe-app-instance-bot` | Describe an app instance bot |
| `list-app-instance-bots` | List app instance bots |
| `update-app-instance-bot` | Update an app instance bot |
| `delete-app-instance-bot` | Delete an app instance bot |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |

## Meetings Commands (`aws chime-sdk-meetings`)

| Command | Description |
|---------|-------------|
| `create-meeting` | Create a meeting |
| `create-meeting-with-attendees` | Create a meeting with attendees |
| `get-meeting` | Get meeting details |
| `delete-meeting` | Delete a meeting |
| `create-attendee` | Add an attendee to a meeting |
| `batch-create-attendee` | Add multiple attendees |
| `get-attendee` | Get attendee details |
| `list-attendees` | List attendees in a meeting |
| `delete-attendee` | Remove an attendee |
| `update-attendee-capabilities` | Update attendee capabilities |
| `batch-update-attendee-capabilities-except` | Update capabilities for all except specified attendees |
| `start-meeting-transcription` | Start meeting transcription |
| `stop-meeting-transcription` | Stop meeting transcription |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |

## Messaging Commands (`aws chime-sdk-messaging`)

| Command | Description |
|---------|-------------|
| `create-channel` | Create a messaging channel |
| `describe-channel` | Describe a channel |
| `list-channels` | List channels |
| `update-channel` | Update a channel |
| `delete-channel` | Delete a channel |
| `search-channels` | Search for channels |
| `list-sub-channels` | List sub-channels of an elastic channel |
| `put-channel-expiration-settings` | Set channel expiration settings |
| `create-channel-membership` | Add a member to a channel |
| `batch-create-channel-membership` | Add multiple members |
| `describe-channel-membership` | Describe a channel membership |
| `list-channel-memberships` | List channel members |
| `delete-channel-membership` | Remove a member from a channel |
| `list-channel-memberships-for-app-instance-user` | List memberships for a user |
| `describe-channel-membership-for-app-instance-user` | Describe membership for a user |
| `get-channel-membership-preferences` | Get member preferences |
| `put-channel-membership-preferences` | Set member preferences |
| `create-channel-moderator` | Add a channel moderator |
| `describe-channel-moderator` | Describe a channel moderator |
| `list-channel-moderators` | List channel moderators |
| `delete-channel-moderator` | Remove a channel moderator |
| `describe-channel-moderated-by-app-instance-user` | Describe channels moderated by a user |
| `list-channels-moderated-by-app-instance-user` | List channels moderated by a user |
| `create-channel-ban` | Ban a user from a channel |
| `describe-channel-ban` | Describe a channel ban |
| `list-channel-bans` | List channel bans |
| `delete-channel-ban` | Remove a channel ban |
| `send-channel-message` | Send a message to a channel |
| `get-channel-message` | Get a channel message |
| `list-channel-messages` | List channel messages |
| `update-channel-message` | Edit a channel message |
| `delete-channel-message` | Delete a channel message |
| `redact-channel-message` | Redact a channel message |
| `get-channel-message-status` | Get message delivery status |
| `update-channel-read-marker` | Update the read marker |
| `create-channel-flow` | Create a channel flow |
| `describe-channel-flow` | Describe a channel flow |
| `list-channel-flows` | List channel flows |
| `update-channel-flow` | Update a channel flow |
| `delete-channel-flow` | Delete a channel flow |
| `associate-channel-flow` | Associate a flow with a channel |
| `disassociate-channel-flow` | Disassociate a flow from a channel |
| `list-channels-associated-with-channel-flow` | List channels using a flow |
| `channel-flow-callback` | Handle channel flow callbacks |
| `get-messaging-session-endpoint` | Get the messaging session endpoint |
| `get-messaging-streaming-configurations` | Get streaming configurations |
| `put-messaging-streaming-configurations` | Set streaming configurations |
| `delete-messaging-streaming-configurations` | Delete streaming configurations |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |

## Voice Commands (`aws chime-sdk-voice`)

| Command | Description |
|---------|-------------|
| `create-voice-connector` | Create a voice connector |
| `get-voice-connector` | Get voice connector details |
| `list-voice-connectors` | List voice connectors |
| `update-voice-connector` | Update a voice connector |
| `delete-voice-connector` | Delete a voice connector |
| `create-voice-connector-group` | Create a voice connector group |
| `get-voice-connector-group` | Get voice connector group details |
| `list-voice-connector-groups` | List voice connector groups |
| `update-voice-connector-group` | Update a voice connector group |
| `delete-voice-connector-group` | Delete a voice connector group |
| `list-available-voice-connector-regions` | List available regions |
| `put-voice-connector-origination` | Set origination settings |
| `get-voice-connector-origination` | Get origination settings |
| `delete-voice-connector-origination` | Delete origination settings |
| `put-voice-connector-termination` | Set termination settings |
| `get-voice-connector-termination` | Get termination settings |
| `delete-voice-connector-termination` | Delete termination settings |
| `get-voice-connector-termination-health` | Get termination health |
| `put-voice-connector-termination-credentials` | Set termination credentials |
| `list-voice-connector-termination-credentials` | List termination credentials |
| `delete-voice-connector-termination-credentials` | Delete termination credentials |
| `put-voice-connector-streaming-configuration` | Set streaming configuration |
| `get-voice-connector-streaming-configuration` | Get streaming configuration |
| `delete-voice-connector-streaming-configuration` | Delete streaming configuration |
| `put-voice-connector-logging-configuration` | Set logging configuration |
| `get-voice-connector-logging-configuration` | Get logging configuration |
| `put-voice-connector-proxy` | Set proxy configuration |
| `get-voice-connector-proxy` | Get proxy configuration |
| `delete-voice-connector-proxy` | Delete proxy configuration |
| `put-voice-connector-emergency-calling-configuration` | Set emergency calling config |
| `get-voice-connector-emergency-calling-configuration` | Get emergency calling config |
| `delete-voice-connector-emergency-calling-configuration` | Delete emergency calling config |
| `put-voice-connector-external-systems-configuration` | Set external systems config |
| `get-voice-connector-external-systems-configuration` | Get external systems config |
| `delete-voice-connector-external-systems-configuration` | Delete external systems config |
| `create-phone-number-order` | Order phone numbers |
| `get-phone-number-order` | Get phone number order details |
| `list-phone-number-orders` | List phone number orders |
| `get-phone-number` | Get phone number details |
| `list-phone-numbers` | List phone numbers |
| `update-phone-number` | Update a phone number |
| `delete-phone-number` | Delete a phone number |
| `batch-delete-phone-number` | Delete multiple phone numbers |
| `batch-update-phone-number` | Update multiple phone numbers |
| `restore-phone-number` | Restore a deleted phone number |
| `search-available-phone-numbers` | Search available phone numbers |
| `list-supported-phone-number-countries` | List supported countries |
| `get-phone-number-settings` | Get phone number settings |
| `update-phone-number-settings` | Update phone number settings |
| `associate-phone-numbers-with-voice-connector` | Associate numbers with a voice connector |
| `disassociate-phone-numbers-from-voice-connector` | Disassociate numbers from a voice connector |
| `associate-phone-numbers-with-voice-connector-group` | Associate numbers with a voice connector group |
| `disassociate-phone-numbers-from-voice-connector-group` | Disassociate numbers from a voice connector group |
| `create-sip-media-application` | Create a SIP media application |
| `get-sip-media-application` | Get SIP media application details |
| `list-sip-media-applications` | List SIP media applications |
| `update-sip-media-application` | Update a SIP media application |
| `delete-sip-media-application` | Delete a SIP media application |
| `create-sip-media-application-call` | Create a SIP media application call |
| `update-sip-media-application-call` | Update a SIP media application call |
| `get-sip-media-application-logging-configuration` | Get SIP logging config |
| `put-sip-media-application-logging-configuration` | Set SIP logging config |
| `create-sip-rule` | Create a SIP rule |
| `get-sip-rule` | Get SIP rule details |
| `list-sip-rules` | List SIP rules |
| `update-sip-rule` | Update a SIP rule |
| `delete-sip-rule` | Delete a SIP rule |
| `create-proxy-session` | Create a proxy session |
| `get-proxy-session` | Get proxy session details |
| `list-proxy-sessions` | List proxy sessions |
| `update-proxy-session` | Update a proxy session |
| `delete-proxy-session` | Delete a proxy session |
| `create-voice-profile` | Create a voice profile |
| `get-voice-profile` | Get voice profile details |
| `list-voice-profiles` | List voice profiles |
| `update-voice-profile` | Update a voice profile |
| `delete-voice-profile` | Delete a voice profile |
| `create-voice-profile-domain` | Create a voice profile domain |
| `get-voice-profile-domain` | Get voice profile domain details |
| `list-voice-profile-domains` | List voice profile domains |
| `update-voice-profile-domain` | Update a voice profile domain |
| `delete-voice-profile-domain` | Delete a voice profile domain |
| `start-speaker-search-task` | Start a speaker search task |
| `get-speaker-search-task` | Get speaker search task details |
| `stop-speaker-search-task` | Stop a speaker search task |
| `start-voice-tone-analysis-task` | Start voice tone analysis |
| `get-voice-tone-analysis-task` | Get voice tone analysis details |
| `stop-voice-tone-analysis-task` | Stop voice tone analysis |
| `get-global-settings` | Get global voice settings |
| `update-global-settings` | Update global voice settings |
| `validate-e911-address` | Validate an E911 address |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |

## Global Options

All commands accept these options:

| Option | Description |
|--------|-------------|
| `--output` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | JMESPath query to filter output |
| `--region` | AWS region |
| `--profile` | Named credential profile |
| `--no-cli-pager` | Disable pager for output |
| `--cli-input-json` | Read parameters from JSON string |
| `--cli-input-yaml` | Read parameters from YAML string |
| `--generate-cli-skeleton` | Print JSON/YAML input skeleton |

## Common Patterns

### List all active meetings
```bash
aws chime-sdk-meetings list-attendees \
    --meeting-id a1b2c3d4-5678-90ab-cdef-EXAMPLE11111 \
    --query 'Attendees[].{Id:AttendeeId,ExternalUserId:ExternalUserId}'
```

### List all channels for an app instance
```bash
aws chime-sdk-messaging list-channels \
    --app-instance-arn arn:aws:chime:us-east-1:123456789012:app-instance/abc123 \
    --chime-bearer arn:aws:chime:us-east-1:123456789012:app-instance/abc123/user/admin \
    --query 'Channels[].{Name:Name,Privacy:Privacy,Mode:Mode}'
```

### Check voice connector health
```bash
aws chime-sdk-voice get-voice-connector-termination-health \
    --voice-connector-id abc123
```
