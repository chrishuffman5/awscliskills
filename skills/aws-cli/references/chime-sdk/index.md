# Amazon Chime SDK — Quick Reference

## All Commands — chime-sdk-identity

| Command | Description |
|---------|-------------|
| `create-app-instance` | Create an app instance |
| `describe-app-instance` | Describe an app instance |
| `list-app-instances` | List app instances |
| `update-app-instance` | Update an app instance |
| `delete-app-instance` | Delete an app instance |
| `get-app-instance-retention-settings` | Get retention settings |
| `put-app-instance-retention-settings` | Set retention settings |
| `create-app-instance-user` | Create an app instance user |
| `describe-app-instance-user` | Describe a user |
| `list-app-instance-users` | List users |
| `update-app-instance-user` | Update a user |
| `delete-app-instance-user` | Delete a user |
| `describe-app-instance-user-endpoint` | Describe user endpoint |
| `list-app-instance-user-endpoints` | List user endpoints |
| `register-app-instance-user-endpoint` | Register user endpoint |
| `update-app-instance-user-endpoint` | Update user endpoint |
| `deregister-app-instance-user-endpoint` | Remove user endpoint |
| `put-app-instance-user-expiration-settings` | Set user expiration |
| `create-app-instance-admin` | Create an admin |
| `describe-app-instance-admin` | Describe an admin |
| `list-app-instance-admins` | List admins |
| `delete-app-instance-admin` | Delete an admin |
| `create-app-instance-bot` | Create a bot |
| `describe-app-instance-bot` | Describe a bot |
| `list-app-instance-bots` | List bots |
| `update-app-instance-bot` | Update a bot |
| `delete-app-instance-bot` | Delete a bot |
| `tag-resource` | Add tags |
| `untag-resource` | Remove tags |
| `list-tags-for-resource` | List tags |

## All Commands — chime-sdk-meetings

| Command | Description |
|---------|-------------|
| `create-meeting` | Create a meeting |
| `create-meeting-with-attendees` | Create meeting with attendees |
| `get-meeting` | Get meeting details |
| `delete-meeting` | Delete a meeting |
| `create-attendee` | Create an attendee |
| `batch-create-attendee` | Batch create attendees |
| `get-attendee` | Get attendee details |
| `list-attendees` | List attendees |
| `delete-attendee` | Delete an attendee |
| `update-attendee-capabilities` | Update attendee capabilities |
| `batch-update-attendee-capabilities-except` | Batch update capabilities |
| `start-meeting-transcription` | Start transcription |
| `stop-meeting-transcription` | Stop transcription |
| `tag-resource` | Add tags |
| `untag-resource` | Remove tags |
| `list-tags-for-resource` | List tags |

## All Commands — chime-sdk-messaging

| Command | Description |
|---------|-------------|
| `create-channel` | Create a channel |
| `describe-channel` | Describe a channel |
| `list-channels` | List channels |
| `update-channel` | Update a channel |
| `delete-channel` | Delete a channel |
| `search-channels` | Search channels |
| `describe-channel-moderated-by-app-instance-user` | Describe moderated channel |
| `list-channels-moderated-by-app-instance-user` | List moderated channels |
| `list-sub-channels` | List sub-channels |
| `put-channel-expiration-settings` | Set channel expiration |
| `create-channel-membership` | Add channel member |
| `batch-create-channel-membership` | Batch add members |
| `describe-channel-membership` | Describe membership |
| `list-channel-memberships` | List memberships |
| `delete-channel-membership` | Remove member |
| `describe-channel-membership-for-app-instance-user` | Describe user membership |
| `list-channel-memberships-for-app-instance-user` | List user memberships |
| `get-channel-membership-preferences` | Get membership preferences |
| `put-channel-membership-preferences` | Set membership preferences |
| `send-channel-message` | Send a message |
| `get-channel-message` | Get a message |
| `list-channel-messages` | List messages |
| `update-channel-message` | Update a message |
| `delete-channel-message` | Delete a message |
| `redact-channel-message` | Redact a message |
| `get-channel-message-status` | Get message status |
| `update-channel-read-marker` | Update read marker |
| `create-channel-flow` | Create a channel flow |
| `describe-channel-flow` | Describe a channel flow |
| `list-channel-flows` | List channel flows |
| `update-channel-flow` | Update a channel flow |
| `delete-channel-flow` | Delete a channel flow |
| `associate-channel-flow` | Associate flow with channel |
| `disassociate-channel-flow` | Remove flow from channel |
| `list-channels-associated-with-channel-flow` | List associated channels |
| `channel-flow-callback` | Channel flow callback |
| `create-channel-ban` | Ban a user from channel |
| `describe-channel-ban` | Describe a ban |
| `list-channel-bans` | List bans |
| `delete-channel-ban` | Remove a ban |
| `create-channel-moderator` | Create a moderator |
| `describe-channel-moderator` | Describe a moderator |
| `list-channel-moderators` | List moderators |
| `delete-channel-moderator` | Delete a moderator |
| `get-messaging-session-endpoint` | Get session endpoint |
| `get-messaging-streaming-configurations` | Get streaming config |
| `put-messaging-streaming-configurations` | Set streaming config |
| `delete-messaging-streaming-configurations` | Delete streaming config |
| `tag-resource` | Add tags |
| `untag-resource` | Remove tags |
| `list-tags-for-resource` | List tags |

## All Commands — chime-sdk-voice

| Command | Description |
|---------|-------------|
| `create-voice-connector` | Create a voice connector |
| `get-voice-connector` | Get voice connector |
| `list-voice-connectors` | List voice connectors |
| `update-voice-connector` | Update voice connector |
| `delete-voice-connector` | Delete voice connector |
| `create-voice-connector-group` | Create connector group |
| `get-voice-connector-group` | Get connector group |
| `list-voice-connector-groups` | List connector groups |
| `update-voice-connector-group` | Update connector group |
| `delete-voice-connector-group` | Delete connector group |
| `get-voice-connector-origination` | Get origination settings |
| `put-voice-connector-origination` | Set origination settings |
| `delete-voice-connector-origination` | Delete origination |
| `get-voice-connector-termination` | Get termination settings |
| `put-voice-connector-termination` | Set termination settings |
| `delete-voice-connector-termination` | Delete termination |
| `list-voice-connector-termination-credentials` | List termination creds |
| `put-voice-connector-termination-credentials` | Set termination creds |
| `delete-voice-connector-termination-credentials` | Delete termination creds |
| `get-voice-connector-proxy` | Get proxy settings |
| `put-voice-connector-proxy` | Set proxy settings |
| `delete-voice-connector-proxy` | Delete proxy |
| `get-voice-connector-streaming-configuration` | Get streaming config |
| `put-voice-connector-streaming-configuration` | Set streaming config |
| `delete-voice-connector-streaming-configuration` | Delete streaming config |
| `get-voice-connector-logging-configuration` | Get logging config |
| `put-voice-connector-logging-configuration` | Set logging config |
| `get-voice-connector-emergency-calling-configuration` | Get E911 config |
| `put-voice-connector-emergency-calling-configuration` | Set E911 config |
| `delete-voice-connector-emergency-calling-configuration` | Delete E911 config |
| `get-voice-connector-external-systems-configuration` | Get external config |
| `put-voice-connector-external-systems-configuration` | Set external config |
| `delete-voice-connector-external-systems-configuration` | Delete external config |
| `get-voice-connector-termination-health` | Get termination health |
| `create-phone-number-order` | Order phone numbers |
| `get-phone-number` | Get phone number |
| `get-phone-number-order` | Get phone number order |
| `list-phone-numbers` | List phone numbers |
| `list-phone-number-orders` | List phone number orders |
| `update-phone-number` | Update phone number |
| `delete-phone-number` | Delete phone number |
| `batch-delete-phone-number` | Batch delete numbers |
| `batch-update-phone-number` | Batch update numbers |
| `restore-phone-number` | Restore deleted number |
| `get-phone-number-settings` | Get phone settings |
| `update-phone-number-settings` | Update phone settings |
| `search-available-phone-numbers` | Search available numbers |
| `list-supported-phone-number-countries` | List supported countries |
| `associate-phone-numbers-with-voice-connector` | Associate numbers to VC |
| `disassociate-phone-numbers-from-voice-connector` | Remove numbers from VC |
| `associate-phone-numbers-with-voice-connector-group` | Associate to VC group |
| `disassociate-phone-numbers-from-voice-connector-group` | Remove from VC group |
| `list-available-voice-connector-regions` | List available regions |
| `get-global-settings` | Get global settings |
| `update-global-settings` | Update global settings |
| `validate-e911-address` | Validate E911 address |
| `create-sip-media-application` | Create SIP media app |
| `get-sip-media-application` | Get SIP media app |
| `list-sip-media-applications` | List SIP media apps |
| `update-sip-media-application` | Update SIP media app |
| `delete-sip-media-application` | Delete SIP media app |
| `get-sip-media-application-logging-configuration` | Get SIP logging |
| `put-sip-media-application-logging-configuration` | Set SIP logging |
| `create-sip-media-application-call` | Create SIP call |
| `update-sip-media-application-call` | Update SIP call |
| `create-sip-rule` | Create SIP rule |
| `get-sip-rule` | Get SIP rule |
| `list-sip-rules` | List SIP rules |
| `update-sip-rule` | Update SIP rule |
| `delete-sip-rule` | Delete SIP rule |
| `create-proxy-session` | Create proxy session |
| `get-proxy-session` | Get proxy session |
| `list-proxy-sessions` | List proxy sessions |
| `update-proxy-session` | Update proxy session |
| `delete-proxy-session` | Delete proxy session |
| `create-voice-profile-domain` | Create voice profile domain |
| `get-voice-profile-domain` | Get voice profile domain |
| `list-voice-profile-domains` | List voice profile domains |
| `update-voice-profile-domain` | Update voice profile domain |
| `delete-voice-profile-domain` | Delete voice profile domain |
| `create-voice-profile` | Create voice profile |
| `get-voice-profile` | Get voice profile |
| `list-voice-profiles` | List voice profiles |
| `update-voice-profile` | Update voice profile |
| `delete-voice-profile` | Delete voice profile |
| `start-speaker-search-task` | Start speaker search |
| `get-speaker-search-task` | Get speaker search task |
| `stop-speaker-search-task` | Stop speaker search |
| `start-voice-tone-analysis-task` | Start voice tone analysis |
| `get-voice-tone-analysis-task` | Get voice tone analysis |
| `stop-voice-tone-analysis-task` | Stop voice tone analysis |
| `tag-resource` | Add tags |
| `untag-resource` | Remove tags |
| `list-tags-for-resource` | List tags |

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

### List all meetings
```bash
aws chime-sdk-meetings list-tags-for-resource \
    --resource-arn MEETING_ARN
```

### Get messaging session endpoint
```bash
aws chime-sdk-messaging get-messaging-session-endpoint
```

### Search available phone numbers
```bash
aws chime-sdk-voice search-available-phone-numbers \
    --phone-number-type Local \
    --country US \
    --area-code 206
```
