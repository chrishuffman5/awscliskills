# AWS CLI v2 — Verified Permissions (Amazon Verified Permissions)

## Overview

Complete reference for all `aws verifiedpermissions` subcommands in AWS CLI v2. Covers policy store management, policy and policy template CRUD, identity source integration with Cognito and OIDC providers, authorization decisions (single and batch), and schema management using the Cedar policy language.

## Quick Reference — Common Workflows

### Create a policy store with strict validation
```bash
aws verifiedpermissions create-policy-store \
  --validation-settings mode=STRICT \
  --description "My application policy store"
```

### Define and upload a schema
```bash
aws verifiedpermissions put-schema \
  --policy-store-id PSEXAMPLEabcdefg111111 \
  --definition cedarJson='{"MyApp":{"entityTypes":{"User":{},"Photo":{"shape":{"type":"Record","attributes":{"owner":{"type":"Entity","name":"MyApp::User"}}}}},"actions":{"view":{"appliesTo":{"principalTypes":["User"],"resourceTypes":["Photo"]}}}}}'
```

### Create a static Cedar policy
```bash
aws verifiedpermissions create-policy \
  --policy-store-id PSEXAMPLEabcdefg111111 \
  --definition '{"static":{"statement":"permit(principal == MyApp::User::\"alice\", action == MyApp::Action::\"view\", resource == MyApp::Photo::\"photo123\");"}}'
```

### Create a policy template
```bash
aws verifiedpermissions create-policy-template \
  --policy-store-id PSEXAMPLEabcdefg111111 \
  --statement 'permit(principal == ?principal, action == MyApp::Action::"view", resource in ?resource);'
```

### Check authorization
```bash
aws verifiedpermissions is-authorized \
  --policy-store-id PSEXAMPLEabcdefg111111 \
  --principal entityType=MyApp::User,entityId=alice \
  --action actionType=MyApp::Action,actionId=view \
  --resource entityType=MyApp::Photo,entityId=photo123
```

### Check authorization with identity token (Cognito/OIDC)
```bash
aws verifiedpermissions is-authorized-with-token \
  --policy-store-id PSEXAMPLEabcdefg111111 \
  --identity-token "$ID_TOKEN" \
  --action actionType=MyApp::Action,actionId=view \
  --resource entityType=MyApp::Photo,entityId=photo123
```

### Connect a Cognito user pool as identity source
```bash
aws verifiedpermissions create-identity-source \
  --policy-store-id PSEXAMPLEabcdefg111111 \
  --configuration '{"cognitoUserPoolConfiguration":{"userPoolArn":"arn:aws:cognito-idp:us-east-1:123456789012:userpool/us-east-1_Example"}}' \
  --principal-entity-type "MyApp::User"
```

### Batch authorization check
```bash
aws verifiedpermissions batch-is-authorized \
  --policy-store-id PSEXAMPLEabcdefg111111 \
  --requests '[{"principal":{"entityType":"MyApp::User","entityId":"alice"},"action":{"actionType":"MyApp::Action","actionId":"view"},"resource":{"entityType":"MyApp::Photo","entityId":"photo1"}},{"principal":{"entityType":"MyApp::User","entityId":"alice"},"action":{"actionType":"MyApp::Action","actionId":"delete"},"resource":{"entityType":"MyApp::Photo","entityId":"photo1"}}]'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Policy Stores | [`policy-stores.md`](policy-stores.md) | create-policy-store, delete-policy-store, get-policy-store, list-policy-stores, update-policy-store |
| Policies | [`policies.md`](policies.md) | create-policy, delete-policy, get-policy, list-policies, update-policy, batch-get-policy |
| Policy Templates | [`policy-templates.md`](policy-templates.md) | create-policy-template, delete-policy-template, get-policy-template, list-policy-templates, update-policy-template |
| Identity Sources | [`identity-sources.md`](identity-sources.md) | create-identity-source, delete-identity-source, get-identity-source, list-identity-sources, update-identity-source |
| Authorization & Tags | [`authorization-tags.md`](authorization-tags.md) | is-authorized, is-authorized-with-token, batch-is-authorized, batch-is-authorized-with-token, get-schema, put-schema, tag-resource, untag-resource, list-tags-for-resource |
