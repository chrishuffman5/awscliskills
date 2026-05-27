# Tags

All four Chime SDK namespaces support tagging via their respective CLI namespaces.

### 18.1 Identity Tags — `aws chime-sdk-identity`

```bash
aws chime-sdk-identity tag-resource --resource-arn <value> --tags <value>
aws chime-sdk-identity untag-resource --resource-arn <value> --tag-keys key1 key2
aws chime-sdk-identity list-tags-for-resource --resource-arn <value>
```

**Taggable resources:** AppInstance, AppInstanceUser, AppInstanceBot

---

### 18.2 Meetings Tags — `aws chime-sdk-meetings`

```bash
aws chime-sdk-meetings tag-resource --resource-arn <value> --tags <value>
aws chime-sdk-meetings untag-resource --resource-arn <value> --tag-keys key1 key2
aws chime-sdk-meetings list-tags-for-resource --resource-arn <value>
```

**Taggable resources:** Meeting

---

### 18.3 Messaging Tags — `aws chime-sdk-messaging`

```bash
aws chime-sdk-messaging tag-resource --resource-arn <value> --tags <value>
aws chime-sdk-messaging untag-resource --resource-arn <value> --tag-keys key1 key2
aws chime-sdk-messaging list-tags-for-resource --resource-arn <value>
```

**Taggable resources:** Channel, ChannelFlow

---

### 18.4 Voice Tags — `aws chime-sdk-voice`

```bash
aws chime-sdk-voice tag-resource --resource-arn <value> --tags <value>
aws chime-sdk-voice untag-resource --resource-arn <value> --tag-keys key1 key2
aws chime-sdk-voice list-tags-for-resource --resource-arn <value>
```

**Taggable resources:** VoiceConnector, VoiceConnectorGroup, SipMediaApplication, VoiceProfileDomain

---

### Common Tag Structure

All namespaces use the same tag structure:

```json
[
    {"Key": "Environment", "Value": "production"},
    {"Key": "Team", "Value": "communications"}
]
```

**Parameters (all namespaces):**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** (tag-resource) | list | -- | Tags (1-50) |
| `--tag-keys` | **Yes** (untag-resource) | list | -- | Tag keys to remove |

**Output Schema (list-tags-for-resource):**
```json
{
    "Tags": [
        {"Key": "string", "Value": "string"}
    ]
}
```
