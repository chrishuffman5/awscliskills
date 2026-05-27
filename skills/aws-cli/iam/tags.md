# Tags

IAM supports tagging on users, roles, policies, instance profiles, MFA devices, OIDC providers, SAML providers, and server certificates. All tag commands follow the same pattern.

### Tag Commands Pattern

**`tag-<resource>`** — Adds or overwrites tags.

```bash
aws iam tag-user --user-name <value> --tags Key=string,Value=string ...
aws iam tag-role --role-name <value> --tags Key=string,Value=string ...
aws iam tag-policy --policy-arn <value> --tags Key=string,Value=string ...
aws iam tag-instance-profile --instance-profile-name <value> --tags Key=string,Value=string ...
aws iam tag-mfa-device --serial-number <value> --tags Key=string,Value=string ...
aws iam tag-open-id-connect-provider --open-id-connect-provider-arn <value> --tags Key=string,Value=string ...
aws iam tag-saml-provider --saml-provider-arn <value> --tags Key=string,Value=string ...
aws iam tag-server-certificate --server-certificate-name <value> --tags Key=string,Value=string ...
```

**Output:** None on success.

---

**`untag-<resource>`** — Removes tags by key.

```bash
aws iam untag-user --user-name <value> --tag-keys Key1 Key2 ...
aws iam untag-role --role-name <value> --tag-keys Key1 Key2 ...
aws iam untag-policy --policy-arn <value> --tag-keys Key1 Key2 ...
aws iam untag-instance-profile --instance-profile-name <value> --tag-keys Key1 Key2 ...
aws iam untag-mfa-device --serial-number <value> --tag-keys Key1 Key2 ...
aws iam untag-open-id-connect-provider --open-id-connect-provider-arn <value> --tag-keys Key1 Key2 ...
aws iam untag-saml-provider --saml-provider-arn <value> --tag-keys Key1 Key2 ...
aws iam untag-server-certificate --server-certificate-name <value> --tag-keys Key1 Key2 ...
```

**Output:** None on success.

---

**`list-<resource>-tags`** — Lists tags. **Paginated.**

```bash
aws iam list-user-tags --user-name <value>
aws iam list-role-tags --role-name <value>
aws iam list-policy-tags --policy-arn <value>
aws iam list-instance-profile-tags --instance-profile-name <value>
aws iam list-mfa-device-tags --serial-number <value>
aws iam list-open-id-connect-provider-tags --open-id-connect-provider-arn <value>
aws iam list-saml-provider-tags --saml-provider-arn <value>
aws iam list-server-certificate-tags --server-certificate-name <value>
```

**Output Schema:**
```json
{
    "Tags": [{ "Key": "string", "Value": "string" }],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

### Tag Limits

- Max 50 tags per resource
- Key: 1-128 chars (Unicode letters, digits, spaces, `_ . : / = + - @`)
- Value: 0-256 chars (same character set)
- Keys are case-sensitive and must be unique per resource

---
