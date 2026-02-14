# Amazon Pinpoint — Quick Reference

## Pinpoint Commands (`aws pinpoint`)

| Command | Description |
|---------|-------------|
| `create-app` | Create a Pinpoint application |
| `get-app` | Get application details |
| `get-apps` | List all applications |
| `delete-app` | Delete an application |
| `update-application-settings` | Update application settings |
| `get-application-settings` | Get application settings |
| `get-application-date-range-kpi` | Get KPI data for an application |
| `create-campaign` | Create a campaign |
| `get-campaign` | Get campaign details |
| `get-campaigns` | List campaigns |
| `update-campaign` | Update a campaign |
| `delete-campaign` | Delete a campaign |
| `get-campaign-activities` | Get campaign activity details |
| `get-campaign-date-range-kpi` | Get KPI data for a campaign |
| `get-campaign-version` | Get a specific campaign version |
| `get-campaign-versions` | List campaign versions |
| `create-journey` | Create a journey |
| `get-journey` | Get journey details |
| `list-journeys` | List journeys |
| `update-journey` | Update a journey |
| `delete-journey` | Delete a journey |
| `update-journey-state` | Update journey state (start/stop) |
| `get-journey-date-range-kpi` | Get KPI data for a journey |
| `get-journey-execution-metrics` | Get journey execution metrics |
| `get-journey-execution-activity-metrics` | Get journey activity execution metrics |
| `get-journey-runs` | List journey runs |
| `get-journey-run-execution-metrics` | Get journey run execution metrics |
| `get-journey-run-execution-activity-metrics` | Get journey run activity metrics |
| `create-segment` | Create a segment |
| `get-segment` | Get segment details |
| `get-segments` | List segments |
| `update-segment` | Update a segment |
| `delete-segment` | Delete a segment |
| `get-segment-version` | Get a specific segment version |
| `get-segment-versions` | List segment versions |
| `get-segment-export-jobs` | List segment export jobs |
| `get-segment-import-jobs` | List segment import jobs |
| `create-email-template` | Create an email template |
| `create-sms-template` | Create an SMS template |
| `create-push-template` | Create a push notification template |
| `create-voice-template` | Create a voice template |
| `create-in-app-template` | Create an in-app message template |
| `get-email-template` | Get an email template |
| `get-sms-template` | Get an SMS template |
| `get-push-template` | Get a push template |
| `get-voice-template` | Get a voice template |
| `get-in-app-template` | Get an in-app template |
| `update-email-template` | Update an email template |
| `update-sms-template` | Update an SMS template |
| `update-push-template` | Update a push template |
| `update-voice-template` | Update a voice template |
| `update-in-app-template` | Update an in-app template |
| `delete-email-template` | Delete an email template |
| `delete-sms-template` | Delete an SMS template |
| `delete-push-template` | Delete a push template |
| `delete-voice-template` | Delete a voice template |
| `delete-in-app-template` | Delete an in-app template |
| `list-templates` | List all templates |
| `list-template-versions` | List template versions |
| `update-template-active-version` | Set the active template version |
| `get-channels` | Get all channel information |
| `get-email-channel` | Get email channel info |
| `update-email-channel` | Update email channel |
| `delete-email-channel` | Delete email channel |
| `get-sms-channel` | Get SMS channel info |
| `update-sms-channel` | Update SMS channel |
| `delete-sms-channel` | Delete SMS channel |
| `get-voice-channel` | Get voice channel info |
| `update-voice-channel` | Update voice channel |
| `delete-voice-channel` | Delete voice channel |
| `get-apns-channel` | Get APNS channel info |
| `update-apns-channel` | Update APNS channel |
| `delete-apns-channel` | Delete APNS channel |
| `get-gcm-channel` | Get GCM/Firebase channel info |
| `update-gcm-channel` | Update GCM channel |
| `delete-gcm-channel` | Delete GCM channel |
| `get-adm-channel` | Get ADM channel info |
| `update-adm-channel` | Update ADM channel |
| `delete-adm-channel` | Delete ADM channel |
| `get-baidu-channel` | Get Baidu channel info |
| `update-baidu-channel` | Update Baidu channel |
| `delete-baidu-channel` | Delete Baidu channel |
| `get-endpoint` | Get endpoint details |
| `update-endpoint` | Update an endpoint |
| `delete-endpoint` | Delete an endpoint |
| `get-user-endpoints` | Get endpoints for a user |
| `delete-user-endpoints` | Delete all endpoints for a user |
| `update-endpoints-batch` | Update endpoints in batch |
| `send-messages` | Send direct messages to addresses/endpoints |
| `send-users-messages` | Send messages to specific users |
| `send-otp-message` | Send OTP verification message |
| `verify-otp-message` | Verify OTP code |
| `put-events` | Record events for endpoints |
| `get-in-app-messages` | Get in-app messages for an endpoint |
| `create-import-job` | Create an endpoint import job |
| `get-import-job` | Get import job details |
| `get-import-jobs` | List import jobs |
| `create-export-job` | Create an endpoint export job |
| `get-export-job` | Get export job details |
| `get-export-jobs` | List export jobs |
| `put-event-stream` | Create/update event stream |
| `get-event-stream` | Get event stream details |
| `delete-event-stream` | Delete event stream |
| `create-recommender-configuration` | Create recommender configuration |
| `get-recommender-configuration` | Get recommender configuration |
| `get-recommender-configurations` | List recommender configurations |
| `update-recommender-configuration` | Update recommender configuration |
| `delete-recommender-configuration` | Delete recommender configuration |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |
| `phone-number-validate` | Validate a phone number |
| `remove-attributes` | Remove attributes from endpoints |

## Pinpoint SMS Voice v2 Commands (`aws pinpoint-sms-voice-v2`)

| Command | Description |
|---------|-------------|
| `send-text-message` | Send an SMS text message |
| `send-voice-message` | Send a voice message |
| `send-media-message` | Send an MMS media message |
| `put-message-feedback` | Provide feedback on a sent message |
| `create-configuration-set` | Create a configuration set |
| `describe-configuration-sets` | Describe configuration sets |
| `delete-configuration-set` | Delete a configuration set |
| `create-event-destination` | Create an event destination |
| `update-event-destination` | Update an event destination |
| `delete-event-destination` | Delete an event destination |
| `create-pool` | Create a phone number pool |
| `describe-pools` | Describe pools |
| `update-pool` | Update a pool |
| `delete-pool` | Delete a pool |
| `list-pool-origination-identities` | List origination identities in a pool |
| `associate-origination-identity` | Associate an origination identity with a pool |
| `disassociate-origination-identity` | Disassociate an origination identity |
| `request-phone-number` | Request a new phone number |
| `describe-phone-numbers` | Describe phone numbers |
| `update-phone-number` | Update a phone number |
| `release-phone-number` | Release a phone number |
| `request-sender-id` | Request a sender ID |
| `describe-sender-ids` | Describe sender IDs |
| `update-sender-id` | Update a sender ID |
| `release-sender-id` | Release a sender ID |
| `create-opt-out-list` | Create an opt-out list |
| `describe-opt-out-lists` | Describe opt-out lists |
| `delete-opt-out-list` | Delete an opt-out list |
| `put-opted-out-number` | Add a number to an opt-out list |
| `delete-opted-out-number` | Remove a number from an opt-out list |
| `describe-opted-out-numbers` | Describe opted-out numbers |
| `put-keyword` | Create or update a keyword |
| `delete-keyword` | Delete a keyword |
| `describe-keywords` | Describe keywords |
| `create-protect-configuration` | Create a protect configuration |
| `describe-protect-configurations` | Describe protect configurations |
| `update-protect-configuration` | Update a protect configuration |
| `delete-protect-configuration` | Delete a protect configuration |
| `create-registration` | Create a registration |
| `describe-registrations` | Describe registrations |
| `delete-registration` | Delete a registration |
| `describe-account-attributes` | Describe account attributes |
| `describe-account-limits` | Describe account limits |
| `describe-spend-limits` | Describe spend limits |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |

## Global Options

These options are available on ALL `aws pinpoint` and `aws pinpoint-sms-voice-v2` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |
