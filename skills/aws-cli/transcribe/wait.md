# Wait

### 7.1 `wait vocabulary-ready`

Polls `get-vocabulary` every 5 seconds until the vocabulary reaches the `READY` state. Exits with return code 255 after 40 failed checks (about 200 seconds).

**Synopsis:**
```bash
aws transcribe wait vocabulary-ready \
    --vocabulary-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vocabulary-name` | **Yes** | string | -- | Name of the vocabulary to wait for |

**Behavior:**
- Polls every **5 seconds**
- Max **40 attempts** (~200 seconds)
- Succeeds when `VocabularyState` is `READY`
- Returns exit code **255** on timeout

**Output:** None (exits with code 0 on success, 255 on timeout)
