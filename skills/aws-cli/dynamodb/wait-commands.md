# Wait Commands

### 18.1 `wait table-exists`

Polls `describe-table` every 20 seconds until the table status is `ACTIVE`. Fails after 25 checks (about 8 minutes).

```bash
aws dynamodb wait table-exists --table-name <value>
```

### 18.2 `wait table-not-exists`

Polls `describe-table` every 20 seconds until `ResourceNotFoundException` is raised (table fully deleted). Fails after 25 checks.

```bash
aws dynamodb wait table-not-exists --table-name <value>
```

---
