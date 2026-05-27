# Proactive Engagement

Proactive engagement allows the Shield Response Team (SRT) to contact you directly during a detected attack, using the emergency contacts you provide.

### 5.1 `enable-proactive-engagement`

Enables proactive engagement with the SRT. You must first provide emergency contact information.

**Synopsis:**
```bash
aws shield enable-proactive-engagement \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:** Empty on success.

---

### 5.2 `disable-proactive-engagement`

Disables proactive engagement. The SRT will not proactively contact you during attacks.

**Synopsis:**
```bash
aws shield disable-proactive-engagement \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:** Empty on success.

---

### 5.3 `associate-proactive-engagement-details`

Initializes proactive engagement and sets the list of emergency contacts. Must be called before enabling proactive engagement.

**Synopsis:**
```bash
aws shield associate-proactive-engagement-details \
    --emergency-contact-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--emergency-contact-list` | **Yes** | list | -- | Emergency contacts (1-10). Shorthand: `EmailAddress=string,PhoneNumber=string,ContactNotes=string ...` |

**Emergency Contact Structure:**
```json
{
    "EmailAddress": "string",
    "PhoneNumber": "string",
    "ContactNotes": "string"
}
```

- `EmailAddress` (required): 1-150 chars
- `PhoneNumber` (optional): 1-16 chars, pattern `^\+[1-9]\d{1,14}$`
- `ContactNotes` (optional): 1-1024 chars

**Output Schema:** Empty on success.

---

### 5.4 `describe-emergency-contact-settings`

Returns the current emergency contact settings.

**Synopsis:**
```bash
aws shield describe-emergency-contact-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No command-specific parameters.

**Output Schema:**
```json
{
    "EmergencyContactList": [
        {
            "EmailAddress": "string",
            "PhoneNumber": "string",
            "ContactNotes": "string"
        }
    ]
}
```

---

### 5.5 `update-emergency-contact-settings`

Updates the emergency contact settings. Replaces the existing list.

**Synopsis:**
```bash
aws shield update-emergency-contact-settings \
    [--emergency-contact-list <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--emergency-contact-list` | No | list | None | Updated emergency contacts (0-10). Pass empty list to clear |

**Output Schema:** Empty on success.

---

### 5.6 `associate-health-check`

Associates a Route 53 health check with a Shield Advanced protection. This allows Shield to use health check status as an additional detection signal.

**Synopsis:**
```bash
aws shield associate-health-check \
    --protection-id <value> \
    --health-check-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protection-id` | **Yes** | string | -- | Protection ID to associate with |
| `--health-check-arn` | **Yes** | string | -- | ARN of the Route 53 health check |

**Output Schema:** Empty on success.

---

### 5.7 `disassociate-health-check`

Removes a Route 53 health check association from a Shield Advanced protection.

**Synopsis:**
```bash
aws shield disassociate-health-check \
    --protection-id <value> \
    --health-check-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protection-id` | **Yes** | string | -- | Protection ID |
| `--health-check-arn` | **Yes** | string | -- | ARN of the health check to disassociate |

**Output Schema:** Empty on success.
