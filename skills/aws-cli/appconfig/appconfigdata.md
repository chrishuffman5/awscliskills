# AppConfigData

The `aws appconfigdata` commands are used to retrieve configuration data at runtime. They provide a simplified interface for applications to poll for configuration updates.

### 10.1 `start-configuration-session`

Starts a configuration session used to retrieve configuration data. A session token is returned for use with `get-latest-configuration`.

**Synopsis:**
```bash
aws appconfigdata start-configuration-session \
    --application-identifier <value> \
    --environment-identifier <value> \
    --configuration-profile-identifier <value> \
    [--required-minimum-poll-interval-in-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-identifier` | **Yes** | string | -- | Application ID or name (1-128 chars) |
| `--environment-identifier` | **Yes** | string | -- | Environment ID or name (1-128 chars) |
| `--configuration-profile-identifier` | **Yes** | string | -- | Configuration profile ID or name (1-128 chars) |
| `--required-minimum-poll-interval-in-seconds` | No | integer | None | Minimum polling interval constraint (15-86400 seconds) |

**Output Schema:**
```json
{
    "InitialConfigurationToken": "string"
}
```

The `InitialConfigurationToken` is valid for up to 24 hours. Use it only once in the first call to `get-latest-configuration`. Subsequent calls must use the `NextPollConfigurationToken` from the response.

---

### 10.2 `get-latest-configuration`

Retrieves the latest deployed configuration data. Returns new data only when the configuration has changed since the last poll. This is a priced API call.

**Synopsis:**
```bash
aws appconfigdata get-latest-configuration \
    --configuration-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>] \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-token` | **Yes** | string | -- | Token from `start-configuration-session` or previous `get-latest-configuration` response |
| `outfile` | **Yes** | string | -- | Filename to save configuration content |

**Output Schema:**
```json
{
    "NextPollConfigurationToken": "string",
    "NextPollIntervalInSeconds": "integer",
    "ContentType": "string",
    "Configuration": "blob",
    "VersionLabel": "string"
}
```

**Important notes:**
- Each configuration token is valid for only one call to `get-latest-configuration`
- Always use the `NextPollConfigurationToken` from the response for the next call
- If the configuration has not changed, `Configuration` will be empty
- Tokens expire after 24 hours; expired tokens return `BadRequestException`
- Respect `NextPollIntervalInSeconds` to avoid throttling
