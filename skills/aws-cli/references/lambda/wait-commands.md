# Wait Commands

Lambda provides waiter commands that poll until a condition is met.

### 14.1 `wait function-exists`

Polls `get-function` every 1 second until the function exists. Exits with return code 255 after 20 failed checks.

```bash
aws lambda wait function-exists --function-name <value>
```

### 14.2 `wait function-active`

Polls `get-function-configuration` every 5 seconds until `State` is `Active`. Exits with return code 255 after 60 failed checks.

```bash
aws lambda wait function-active --function-name <value>
```

### 14.3 `wait function-active-v2`

Polls `get-function` every 1 second until `State` is `Active`. Exits with return code 255 after 300 failed checks.

```bash
aws lambda wait function-active-v2 --function-name <value>
```

### 14.4 `wait function-updated`

Polls `get-function-configuration` every 5 seconds until `LastUpdateStatus` is `Successful`. Exits with return code 255 after 60 failed checks.

```bash
aws lambda wait function-updated --function-name <value>
```

### 14.5 `wait function-updated-v2`

Polls `get-function` every 1 second until `LastUpdateStatus` is `Successful`. Exits with return code 255 after 300 failed checks.

```bash
aws lambda wait function-updated-v2 --function-name <value>
```

### 14.6 `wait published-version-active`

Polls `get-function-configuration` every 5 seconds until `State` is `Active` for a published version. Exits with return code 255 after 312 failed checks.

```bash
aws lambda wait published-version-active --function-name <value> --qualifier <version>
```

---
