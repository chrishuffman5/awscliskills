# AWS CLI v2 — SES v2 (Simple Email Service v2)

## Overview

Complete reference for all `aws sesv2` subcommands in AWS CLI v2. Covers email identity management, configuration sets, contact lists, email templates, sending operations, suppression list management, dedicated IPs, and account-level settings.

## Quick Reference — Common Workflows

### Verify an email identity
```bash
aws sesv2 create-email-identity --email-identity user@example.com
```

### Verify a domain identity
```bash
aws sesv2 create-email-identity --email-identity example.com
```

### Send a simple email
```bash
aws sesv2 send-email \
  --from-email-address sender@example.com \
  --destination ToAddresses=recipient@example.com \
  --content "Simple={Subject={Data=Hello},Body={Text={Data=Hello World}}}"
```

### Send a templated email
```bash
aws sesv2 send-email \
  --from-email-address sender@example.com \
  --destination ToAddresses=recipient@example.com \
  --content "Template={TemplateName=my-template,TemplateData='{\"name\":\"John\"}'}"
```

### Create a configuration set
```bash
aws sesv2 create-configuration-set --configuration-set-name my-config-set \
  --delivery-options TlsPolicy=REQUIRE \
  --reputation-options ReputationMetricsEnabled=true \
  --sending-options SendingEnabled=true
```

### Create a contact list
```bash
aws sesv2 create-contact-list --contact-list-name my-contacts \
  --topics Name=Newsletter,DisplayName="Weekly Newsletter",DefaultSubscriptionStatus=OPT_IN
```

### Create an email template
```bash
aws sesv2 create-email-template --template-name my-template \
  --template-content "Subject=Welcome {{name}},Text=Hello {{name}},Html=<h1>Hello {{name}}</h1>"
```

### Check account sending quota
```bash
aws sesv2 get-account --query 'SendQuota'
```

### Add email to suppression list
```bash
aws sesv2 put-suppressed-destination \
  --email-address bounce@example.com \
  --reason BOUNCE
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Email Identities | [`email-identities.md`](email-identities.md) | create-email-identity, delete-email-identity, get-email-identity, list-email-identities, put-email-identity-dkim-attributes, put-email-identity-dkim-signing-attributes, put-email-identity-feedback-attributes, put-email-identity-mail-from-attributes, put-email-identity-configuration-set-attributes |
| Configuration Sets | [`configuration-sets.md`](configuration-sets.md) | create-configuration-set, delete-configuration-set, get-configuration-set, list-configuration-sets, create-configuration-set-event-destination, delete-configuration-set-event-destination, get-configuration-set-event-destinations, update-configuration-set-event-destination |
| Contact Lists | [`contact-lists.md`](contact-lists.md) | create-contact-list, delete-contact-list, get-contact-list, list-contact-lists, update-contact-list, create-contact, delete-contact, get-contact, list-contacts, update-contact |
| Email Templates | [`email-templates.md`](email-templates.md) | create-email-template, delete-email-template, get-email-template, list-email-templates, update-email-template, test-render-email-template |
| Sending | [`sending.md`](sending.md) | send-email, send-bulk-email, create-deliverability-test-report, get-deliverability-test-report, list-deliverability-test-reports |
| Suppression | [`suppression.md`](suppression.md) | put-suppressed-destination, get-suppressed-destination, delete-suppressed-destination, list-suppressed-destinations, put-account-suppression-attributes |
| Dedicated IPs | [`dedicated-ips.md`](dedicated-ips.md) | get-dedicated-ip, list-dedicated-ip-pools, get-dedicated-ips, create-dedicated-ip-pool, delete-dedicated-ip-pool, put-dedicated-ip-in-pool, put-dedicated-ip-warmup-attributes |
| Account | [`account.md`](account.md) | get-account, put-account-details, put-account-dedicated-ip-warmup-attributes, put-account-sending-attributes, put-account-vdm-attributes, get-domain-statistics-report, list-domain-deliverability-campaigns |
