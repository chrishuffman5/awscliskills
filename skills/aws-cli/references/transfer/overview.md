# AWS CLI v2 — Transfer Family

## Overview

Complete reference for all `aws transfer` subcommands in AWS CLI v2. AWS Transfer Family provides managed file transfer services supporting SFTP, FTPS, FTP, and AS2 protocols. Transfer to and from Amazon S3 or Amazon EFS. Covers server management, user provisioning, connectors for SFTP/AS2, workflows for post-upload processing, AS2 profiles and agreements, host keys, certificates, and web apps.

## Quick Reference — Common Workflows

### Create an SFTP server with S3 storage
```bash
aws transfer create-server \
  --protocols SFTP \
  --domain S3 \
  --identity-provider-type SERVICE_MANAGED \
  --endpoint-type PUBLIC \
  --logging-role arn:aws:iam::123456789012:role/TransferLoggingRole \
  --tags Key=Environment,Value=production
```

### Create a user on a server
```bash
aws transfer create-user \
  --server-id s-0123456789abcdef0 \
  --user-name myuser \
  --role arn:aws:iam::123456789012:role/TransferUserRole \
  --home-directory-type PATH \
  --home-directory /my-bucket/home/myuser \
  --ssh-public-key-body "ssh-rsa AAAA..."
```

### Create a VPC endpoint server with EFS
```bash
aws transfer create-server \
  --protocols SFTP \
  --domain EFS \
  --endpoint-type VPC \
  --endpoint-details VpcId=vpc-abc123,SubnetIds=subnet-123,subnet-456,SecurityGroupIds=sg-789 \
  --identity-provider-type SERVICE_MANAGED
```

### Create an SFTP connector
```bash
aws transfer create-connector \
  --url sftp://partner.example.com \
  --access-role arn:aws:iam::123456789012:role/TransferConnectorRole \
  --sftp-config '{"UserSecretId":"arn:aws:secretsmanager:us-east-1:123456789012:secret:my-sftp-creds","TrustedHostKeys":["ssh-rsa AAAA..."]}'
```

### Create an AS2 agreement
```bash
aws transfer create-profile --as2-id MyCompany --profile-type LOCAL \
  --certificate-ids cert-0123456789abcdef0

aws transfer create-profile --as2-id PartnerOrg --profile-type PARTNER \
  --certificate-ids cert-abcdef0123456789a

aws transfer create-agreement \
  --server-id s-0123456789abcdef0 \
  --local-profile-id p-0123456789abcdef0 \
  --partner-profile-id p-abcdef0123456789a \
  --base-directory /my-bucket/as2-inbox \
  --access-role arn:aws:iam::123456789012:role/TransferAS2Role \
  --status ACTIVE
```

### Create a post-upload workflow
```bash
aws transfer create-workflow \
  --steps '[{"Type":"COPY","CopyStepDetails":{"Name":"CopyToArchive","DestinationFileLocation":{"S3FileLocation":{"Bucket":"archive-bucket","Key":"archive/"}},"OverwriteExisting":"TRUE"}},{"Type":"TAG","TagStepDetails":{"Name":"TagFile","Tags":[{"Key":"Status","Value":"Processed"}]}}]' \
  --description "Copy uploaded files to archive and tag"
```

### Start and stop a server
```bash
aws transfer start-server --server-id s-0123456789abcdef0
aws transfer wait server-online --server-id s-0123456789abcdef0

aws transfer stop-server --server-id s-0123456789abcdef0
aws transfer wait server-offline --server-id s-0123456789abcdef0
```

### Start a file transfer via connector
```bash
aws transfer start-file-transfer \
  --connector-id c-0123456789abcdef0 \
  --send-file-paths /my-bucket/outbound/file.csv
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Servers | [`servers.md`](servers.md) | create-server, delete-server, describe-server, list-servers, update-server, start-server, stop-server, describe-security-policy, list-security-policies, test-identity-provider |
| Users | [`users.md`](users.md) | create-user, delete-user, describe-user, list-users, update-user, import-ssh-public-key, delete-ssh-public-key |
| Access | [`access.md`](access.md) | create-access, delete-access, describe-access, list-accesses, update-access |
| Connectors | [`connectors.md`](connectors.md) | create-connector, delete-connector, describe-connector, list-connectors, update-connector, start-file-transfer, start-directory-listing, start-remote-delete, start-remote-move, test-connection, list-file-transfer-results |
| Agreements | [`agreements.md`](agreements.md) | create-agreement, delete-agreement, describe-agreement, list-agreements, update-agreement |
| Profiles | [`profiles.md`](profiles.md) | create-profile, delete-profile, describe-profile, list-profiles, update-profile |
| Workflows | [`workflows.md`](workflows.md) | create-workflow, delete-workflow, describe-workflow, list-workflows, describe-execution, list-executions, send-workflow-step-state |
| Host Keys | [`host-keys.md`](host-keys.md) | import-host-key, delete-host-key, describe-host-key, list-host-keys, update-host-key |
| Certificates | [`certificates.md`](certificates.md) | import-certificate, delete-certificate, describe-certificate, list-certificates, update-certificate |
| Web Apps | [`web-apps.md`](web-apps.md) | create-web-app, delete-web-app, describe-web-app, list-web-apps, update-web-app, describe-web-app-customization, update-web-app-customization, delete-web-app-customization |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait server-online, wait server-offline |
