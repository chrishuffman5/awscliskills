# Channels

Channel commands follow a consistent pattern per channel type: get, update, and delete. Each channel has its own configuration requirements.

### 6.1 `get-channels`

Gets all channel information for an application.

**Synopsis:**
```bash
aws pinpoint get-channels \
    --application-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |

**Output Schema:**
```json
{
    "ChannelsResponse": {
        "Channels": {
            "string": {
                "ApplicationId": "string",
                "CreationDate": "string",
                "Enabled": "boolean",
                "Id": "string",
                "LastModifiedDate": "string",
                "Version": "integer"
            }
        }
    }
}
```

---

### Email Channel (6.2-6.4)

```bash
aws pinpoint get-email-channel --application-id <value>
aws pinpoint update-email-channel --application-id <value> --email-channel-request <value>
aws pinpoint delete-email-channel --application-id <value>
```

**EmailChannelRequest Fields:**
- `FromAddress` (string, **required**): Verified sender email address
- `Identity` (string, **required**): ARN of the Amazon SES verified identity
- `Enabled` (boolean): Enable the channel
- `ConfigurationSet` (string): SES configuration set name
- `RoleArn` (string): IAM role ARN for sending through SES

---

### SMS Channel (6.5-6.7)

```bash
aws pinpoint get-sms-channel --application-id <value>
aws pinpoint update-sms-channel --application-id <value> --sms-channel-request <value>
aws pinpoint delete-sms-channel --application-id <value>
```

**SMSChannelRequest Fields:**
- `Enabled` (boolean): Enable the channel
- `SenderId` (string): Sender ID
- `ShortCode` (string): Short code

---

### Voice Channel (6.8-6.10)

```bash
aws pinpoint get-voice-channel --application-id <value>
aws pinpoint update-voice-channel --application-id <value> --voice-channel-request <value>
aws pinpoint delete-voice-channel --application-id <value>
```

---

### APNS Channel (6.11-6.13)

```bash
aws pinpoint get-apns-channel --application-id <value>
aws pinpoint update-apns-channel --application-id <value> --apns-channel-request <value>
aws pinpoint delete-apns-channel --application-id <value>
```

**APNSChannelRequest Fields:**
- `BundleId` (string): Bundle ID from Apple
- `Certificate` (string): APNs client certificate (PEM)
- `DefaultAuthenticationMethod` (string): `CERTIFICATE` or `TOKEN`
- `Enabled` (boolean): Enable the channel
- `PrivateKey` (string): APNs client certificate private key
- `TeamId` (string): Apple developer team ID
- `TokenKey` (string): APNs auth key (.p8)
- `TokenKeyId` (string): Key ID for the auth key

---

### GCM/Firebase Channel (6.14-6.16)

```bash
aws pinpoint get-gcm-channel --application-id <value>
aws pinpoint update-gcm-channel --application-id <value> --gcm-channel-request <value>
aws pinpoint delete-gcm-channel --application-id <value>
```

**GCMChannelRequest Fields:**
- `ApiKey` (string): FCM/GCM API key (legacy)
- `DefaultAuthenticationMethod` (string): `KEY` or `TOKEN`
- `Enabled` (boolean): Enable the channel
- `ServiceJson` (string): FCM service account JSON credentials

---

### ADM Channel (6.17-6.19)

```bash
aws pinpoint get-adm-channel --application-id <value>
aws pinpoint update-adm-channel --application-id <value> --adm-channel-request <value>
aws pinpoint delete-adm-channel --application-id <value>
```

**ADMChannelRequest Fields:**
- `ClientId` (string, **required**): Amazon client ID from Developer Portal
- `ClientSecret` (string, **required**): Amazon client secret
- `Enabled` (boolean): Enable the channel

---

### Baidu Channel (6.20-6.22)

```bash
aws pinpoint get-baidu-channel --application-id <value>
aws pinpoint update-baidu-channel --application-id <value> --baidu-channel-request <value>
aws pinpoint delete-baidu-channel --application-id <value>
```

**BaiduChannelRequest Fields:**
- `ApiKey` (string, **required**): Baidu API key
- `SecretKey` (string, **required**): Baidu secret key
- `Enabled` (boolean): Enable the channel

---

### APNS Sandbox/VoIP Channels (6.23-6.31)

Follow the same pattern as APNS channel with sandbox/VoIP variants:
- `get-apns-sandbox-channel`, `update-apns-sandbox-channel`, `delete-apns-sandbox-channel`
- `get-apns-voip-channel`, `update-apns-voip-channel`, `delete-apns-voip-channel`
- `get-apns-voip-sandbox-channel`, `update-apns-voip-sandbox-channel`, `delete-apns-voip-sandbox-channel`
