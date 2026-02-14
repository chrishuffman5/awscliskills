# AWS CLI v2 — Amazon Connect

## Overview

Complete reference for `aws connect`, `aws connect-contact-lens`, `aws connectcases`, and `aws connectparticipant` subcommands in AWS CLI v2. Amazon Connect is a cloud-based contact center service that enables customer engagement through voice, chat, task, and email channels. It provides agent management, routing, analytics, evaluation, and integration capabilities. Connect Contact Lens provides real-time and post-call/chat analytics. Connect Cases manages customer issues as cases. Connect Participant enables real-time chat and messaging for participants.

## Quick Reference — Common Workflows

### Create an instance and configure basics
```bash
aws connect create-instance \
    --identity-management-type CONNECT_MANAGED \
    --instance-alias my-contact-center \
    --inbound-calls-enabled \
    --outbound-calls-enabled

aws connect create-hours-of-operation \
    --instance-id INSTANCE_ID \
    --name "Business Hours" \
    --time-zone "America/New_York" \
    --config '[{"Day":"MONDAY","StartTime":{"Hours":9,"Minutes":0},"EndTime":{"Hours":17,"Minutes":0}},{"Day":"TUESDAY","StartTime":{"Hours":9,"Minutes":0},"EndTime":{"Hours":17,"Minutes":0}}]'
```

### Create a queue and routing profile
```bash
aws connect create-queue \
    --instance-id INSTANCE_ID \
    --name "Support Queue" \
    --hours-of-operation-id HOP_ID \
    --description "General support queue"

aws connect create-routing-profile \
    --instance-id INSTANCE_ID \
    --name "Support Routing" \
    --description "Routes to support queue" \
    --default-outbound-queue-id QUEUE_ID \
    --media-concurrencies '[{"Channel":"VOICE","Concurrency":1},{"Channel":"CHAT","Concurrency":3}]'
```

### Create users and agent statuses
```bash
aws connect create-user \
    --username agent01 \
    --password 'P@ssw0rd123' \
    --identity-info FirstName=Jane,LastName=Doe \
    --phone-config PhoneType=SOFT_PHONE,AutoAccept=true,AfterContactWorkTimeLimit=30 \
    --security-profile-ids SECURITY_PROFILE_ID \
    --routing-profile-id ROUTING_PROFILE_ID \
    --instance-id INSTANCE_ID

aws connect create-agent-status \
    --instance-id INSTANCE_ID \
    --name "On Break" \
    --state ENABLED \
    --description "Agent is on break"
```

### Create a contact flow and start outbound call
```bash
aws connect create-contact-flow \
    --instance-id INSTANCE_ID \
    --name "Outbound Flow" \
    --type CONTACT_FLOW \
    --content '{"Version":"2019-10-30","StartAction":"action1","Actions":[...]}'

aws connect start-outbound-voice-contact \
    --instance-id INSTANCE_ID \
    --contact-flow-id FLOW_ID \
    --destination-phone-number "+12025551234" \
    --source-phone-number "+12025555678"
```

### Get historical metrics
```bash
aws connect get-metric-data-v2 \
    --resource-arn arn:aws:connect:us-east-1:123456789012:instance/INSTANCE_ID \
    --start-time 1700000000 \
    --end-time 1700086400 \
    --filters '[{"FilterKey":"QUEUE","FilterValues":["QUEUE_ARN"]}]' \
    --metrics '[{"Name":"CONTACTS_HANDLED"},{"Name":"AVG_HANDLE_TIME"}]'
```

### Create a Cases domain and case
```bash
aws connectcases create-domain --name my-cases-domain

aws connectcases create-case \
    --domain-id DOMAIN_ID \
    --template-id TEMPLATE_ID \
    --fields '[{"id":"title","value":{"stringValue":"Customer Issue"}}]'
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Instances | [instances.md](instances.md) | `create-instance`, `describe-instance`, `list-instances`, `delete-instance`, `describe-instance-attribute`, `list-instance-attributes`, `update-instance-attribute`, `describe-instance-storage-config`, `list-instance-storage-configs`, `associate-instance-storage-config`, `update-instance-storage-config`, `disassociate-instance-storage-config`, `replicate-instance` |
| Contact Flows | [contact-flows.md](contact-flows.md) | `create-contact-flow`, `describe-contact-flow`, `list-contact-flows`, `update-contact-flow-content`, `update-contact-flow-metadata`, `update-contact-flow-name`, `delete-contact-flow`, `create-contact-flow-version`, `list-contact-flow-versions`, `delete-contact-flow-version`, `create-contact-flow-module`, `describe-contact-flow-module`, `list-contact-flow-modules`, `update-contact-flow-module-content`, `update-contact-flow-module-metadata`, `delete-contact-flow-module`, `create-contact-flow-module-alias`, `describe-contact-flow-module-alias`, `list-contact-flow-module-aliases`, `update-contact-flow-module-alias`, `delete-contact-flow-module-alias`, `create-contact-flow-module-version`, `list-contact-flow-module-versions`, `delete-contact-flow-module-version`, `search-contact-flows`, `search-contact-flow-modules` |
| Contacts | [contacts.md](contacts.md) | `create-contact`, `describe-contact`, `list-associated-contacts`, `update-contact`, `update-contact-attributes`, `get-contact-attributes`, `update-contact-routing-data`, `update-contact-schedule`, `stop-contact`, `transfer-contact`, `monitor-contact`, `pause-contact`, `resume-contact`, `tag-contact`, `untag-contact`, `search-contacts`, `batch-put-contact`, `send-chat-integration-event`, `dismiss-user-contact`, `create-persistent-contact-association`, `create-participant`, `get-contact-metrics` |
| Contact Recording | [contact-recording.md](contact-recording.md) | `start-contact-recording`, `stop-contact-recording`, `suspend-contact-recording`, `resume-contact-recording`, `start-contact-streaming`, `stop-contact-streaming`, `start-contact-media-processing`, `stop-contact-media-processing`, `start-screen-sharing`, `list-realtime-contact-analysis-segments-v2`, `list-contact-references` |
| Users | [users.md](users.md) | `create-user`, `describe-user`, `list-users`, `update-user-config`, `update-user-hierarchy`, `update-user-identity-info`, `update-user-phone-config`, `update-user-routing-profile`, `update-user-security-profiles`, `delete-user`, `put-user-status`, `get-current-user-data`, `search-users`, `create-user-hierarchy-group`, `describe-user-hierarchy-group`, `list-user-hierarchy-groups`, `update-user-hierarchy-group-name`, `delete-user-hierarchy-group`, `describe-user-hierarchy-structure`, `update-user-hierarchy-structure`, `search-user-hierarchy-groups`, `associate-user-proficiencies`, `list-user-proficiencies`, `update-user-proficiencies`, `disassociate-user-proficiencies` |
| Queues | [queues.md](queues.md) | `create-queue`, `describe-queue`, `list-queues`, `update-queue-hours-of-operation`, `update-queue-max-contacts`, `update-queue-name`, `update-queue-outbound-caller-config`, `update-queue-outbound-email-config`, `update-queue-status`, `delete-queue`, `search-queues`, `associate-queue-quick-connects`, `list-queue-quick-connects`, `disassociate-queue-quick-connects` |
| Routing Profiles | [routing-profiles.md](routing-profiles.md) | `create-routing-profile`, `describe-routing-profile`, `list-routing-profiles`, `update-routing-profile-name`, `update-routing-profile-default-outbound-queue`, `update-routing-profile-concurrency`, `update-routing-profile-queues`, `update-routing-profile-agent-availability-timer`, `delete-routing-profile`, `associate-routing-profile-queues`, `list-routing-profile-queues`, `list-routing-profile-manual-assignment-queues`, `disassociate-routing-profile-queues`, `search-routing-profiles` |
| Quick Connects | [quick-connects.md](quick-connects.md) | `create-quick-connect`, `describe-quick-connect`, `list-quick-connects`, `update-quick-connect-config`, `update-quick-connect-name`, `delete-quick-connect`, `search-quick-connects` |
| Hours of Operation | [hours-of-operation.md](hours-of-operation.md) | `create-hours-of-operation`, `describe-hours-of-operation`, `list-hours-of-operations`, `update-hours-of-operation`, `delete-hours-of-operation`, `create-hours-of-operation-override`, `describe-hours-of-operation-override`, `list-hours-of-operation-overrides`, `update-hours-of-operation-override`, `delete-hours-of-operation-override`, `search-hours-of-operations`, `search-hours-of-operation-overrides`, `get-effective-hours-of-operations`, `list-child-hours-of-operations`, `associate-hours-of-operations`, `disassociate-hours-of-operations` |
| Agent Status | [agent-status.md](agent-status.md) | `create-agent-status`, `describe-agent-status`, `list-agent-statuses`, `update-agent-status`, `search-agent-statuses` |
| Security Profiles | [security-profiles.md](security-profiles.md) | `create-security-profile`, `describe-security-profile`, `list-security-profiles`, `update-security-profile`, `delete-security-profile`, `search-security-profiles`, `list-security-profile-permissions`, `list-security-profile-applications`, `list-security-profile-flow-modules`, `list-security-keys`, `associate-security-key`, `disassociate-security-key`, `associate-security-profiles`, `disassociate-security-profiles`, `list-entity-security-profiles` |
| Evaluation Forms | [evaluation-forms.md](evaluation-forms.md) | `create-evaluation-form`, `describe-evaluation-form`, `list-evaluation-forms`, `list-evaluation-form-versions`, `update-evaluation-form`, `activate-evaluation-form`, `deactivate-evaluation-form`, `delete-evaluation-form`, `start-contact-evaluation`, `describe-contact-evaluation`, `list-contact-evaluations`, `update-contact-evaluation`, `submit-contact-evaluation`, `delete-contact-evaluation`, `search-contact-evaluations`, `search-evaluation-forms` |
| Prompts & Vocabularies | [prompts-vocabularies.md](prompts-vocabularies.md) | `create-prompt`, `describe-prompt`, `list-prompts`, `update-prompt`, `delete-prompt`, `get-prompt-file`, `search-prompts`, `create-vocabulary`, `describe-vocabulary`, `list-default-vocabularies`, `delete-vocabulary`, `search-vocabularies`, `associate-default-vocabulary` |
| Phone Numbers | [phone-numbers.md](phone-numbers.md) | `claim-phone-number`, `describe-phone-number`, `list-phone-numbers`, `list-phone-numbers-v2`, `update-phone-number`, `update-phone-number-metadata`, `release-phone-number`, `import-phone-number`, `search-available-phone-numbers`, `associate-phone-number-contact-flow`, `disassociate-phone-number-contact-flow` |
| Rules & Templates | [rules-templates.md](rules-templates.md) | `create-rule`, `describe-rule`, `list-rules`, `update-rule`, `delete-rule`, `create-task-template`, `get-task-template`, `list-task-templates`, `update-task-template`, `delete-task-template` |
| Predefined Attributes | [predefined-attributes.md](predefined-attributes.md) | `create-predefined-attribute`, `describe-predefined-attribute`, `list-predefined-attributes`, `update-predefined-attribute`, `delete-predefined-attribute`, `search-predefined-attributes` |
| Integrations | [integrations.md](integrations.md) | `create-integration-association`, `list-integration-associations`, `delete-integration-association`, `associate-lambda-function`, `list-lambda-functions`, `disassociate-lambda-function`, `associate-lex-bot`, `list-lex-bots`, `disassociate-lex-bot`, `associate-bot`, `list-bots`, `disassociate-bot`, `create-use-case`, `list-use-cases`, `delete-use-case`, `associate-approved-origin`, `list-approved-origins`, `disassociate-approved-origin` |
| Traffic Distribution | [traffic-distribution.md](traffic-distribution.md) | `create-traffic-distribution-group`, `describe-traffic-distribution-group`, `list-traffic-distribution-groups`, `delete-traffic-distribution-group`, `get-traffic-distribution`, `update-traffic-distribution`, `associate-traffic-distribution-group-user`, `list-traffic-distribution-group-users`, `disassociate-traffic-distribution-group-user` |
| Metrics | [metrics.md](metrics.md) | `get-current-metric-data`, `get-metric-data`, `get-metric-data-v2`, `get-federation-token` |
| Views | [views.md](views.md) | `create-view`, `describe-view`, `list-views`, `update-view-content`, `update-view-metadata`, `delete-view`, `create-view-version`, `list-view-versions`, `delete-view-version`, `search-views` |
| Email | [email.md](email.md) | `create-email-address`, `describe-email-address`, `update-email-address-metadata`, `delete-email-address`, `search-email-addresses`, `associate-email-address-alias`, `disassociate-email-address-alias`, `start-email-contact`, `start-outbound-email-contact`, `send-outbound-email` |
| Data Tables | [data-tables.md](data-tables.md) | `create-data-table`, `describe-data-table`, `list-data-tables`, `update-data-table-metadata`, `delete-data-table`, `search-data-tables`, `create-data-table-attribute`, `describe-data-table-attribute`, `list-data-table-attributes`, `update-data-table-attribute`, `delete-data-table-attribute`, `list-data-table-primary-values`, `update-data-table-primary-values`, `list-data-table-values`, `batch-create-data-table-value`, `batch-describe-data-table-value`, `batch-update-data-table-value`, `batch-delete-data-table-value`, `evaluate-data-table-values` |
| Workspaces | [workspaces.md](workspaces.md) | `create-workspace`, `describe-workspace`, `list-workspaces`, `update-workspace-metadata`, `update-workspace-visibility`, `update-workspace-theme`, `delete-workspace`, `search-workspaces`, `search-workspace-associations`, `associate-workspace`, `disassociate-workspace`, `create-workspace-page`, `list-workspace-pages`, `update-workspace-page`, `delete-workspace-page`, `import-workspace-media`, `list-workspace-media`, `delete-workspace-media` |
| Testing | [testing.md](testing.md) | `create-test-case`, `describe-test-case`, `list-test-cases`, `update-test-case`, `delete-test-case`, `search-test-cases`, `start-test-case-execution`, `stop-test-case-execution`, `list-test-case-executions`, `list-test-case-execution-records`, `get-test-case-execution-summary` |
| Authentication | [authentication.md](authentication.md) | `describe-authentication-profile`, `list-authentication-profiles`, `update-authentication-profile`, `update-participant-authentication` |
| Analytics | [analytics.md](analytics.md) | `associate-analytics-data-set`, `batch-associate-analytics-data-set`, `list-analytics-data-associations`, `list-analytics-data-lake-data-sets`, `disassociate-analytics-data-set`, `batch-disassociate-analytics-data-set`, `associate-flow`, `get-flow-association`, `list-flow-associations`, `batch-get-flow-association`, `disassociate-flow` |
| Attached Files | [attached-files.md](attached-files.md) | `start-attached-file-upload`, `complete-attached-file-upload`, `get-attached-file`, `delete-attached-file`, `batch-get-attached-file-metadata` |
| Misc | [misc.md](misc.md) | `start-outbound-voice-contact`, `start-chat-contact`, `start-task-contact`, `start-web-rtc-contact`, `start-outbound-chat-contact`, `create-notification`, `describe-notification`, `list-notifications`, `update-notification-content`, `delete-notification`, `search-notifications`, `list-user-notifications`, `update-user-notification-status`, `create-push-notification-registration`, `delete-push-notification-registration`, `search-resource-tags`, `update-participant-role-config`, `list-contact-evaluations` |
| Contact Lens | [contact-lens.md](contact-lens.md) | `list-realtime-contact-analysis-segments` (connect-contact-lens) |
| Cases | [cases.md](cases.md) | `create-case`, `get-case`, `search-cases`, `update-case`, `delete-case`, `get-case-audit-events`, `list-cases-for-contact`, `search-related-items`, `search-all-related-items`, `create-related-item`, `delete-related-item`, `create-domain`, `get-domain`, `list-domains`, `delete-domain`, `create-template`, `get-template`, `list-templates`, `update-template`, `delete-template`, `create-field`, `batch-get-field`, `list-fields`, `update-field`, `delete-field`, `list-field-options`, `batch-put-field-options`, `create-layout`, `get-layout`, `list-layouts`, `update-layout`, `delete-layout`, `create-case-rule`, `batch-get-case-rule`, `list-case-rules`, `update-case-rule`, `delete-case-rule`, `get-case-event-configuration`, `put-case-event-configuration` (connectcases) |
| Participant | [participant.md](participant.md) | `create-participant-connection`, `send-message`, `send-event`, `get-transcript`, `get-attachment`, `start-attachment-upload`, `complete-attachment-upload`, `disconnect-participant`, `describe-view`, `get-authentication-url`, `cancel-participant-authentication` (connectparticipant) |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` (connect), `tag-resource`, `untag-resource`, `list-tags-for-resource` (connectcases) |
