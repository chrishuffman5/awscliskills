# Wait Commands

### 10.1 `wait load-balancer-available`

Polls `describe-load-balancers` every 15 seconds until the load balancer state is `active`. Exits with return code 255 after 40 failed checks.

**Synopsis:**
```bash
aws elbv2 wait load-balancer-available \
    [--load-balancer-arns <value>] \
    [--names <value>]
```

---

### 10.2 `wait load-balancer-exists`

Polls `describe-load-balancers` every 15 seconds until a successful response is received (HTTP 200). Exits with return code 255 after 40 failed checks.

**Synopsis:**
```bash
aws elbv2 wait load-balancer-exists \
    [--load-balancer-arns <value>] \
    [--names <value>]
```

---

### 10.3 `wait load-balancers-deleted`

Polls `describe-load-balancers` every 15 seconds until a `LoadBalancerNotFound` error is received. Exits with return code 255 after 40 failed checks.

**Synopsis:**
```bash
aws elbv2 wait load-balancers-deleted \
    [--load-balancer-arns <value>] \
    [--names <value>]
```

---

### 10.4 `wait target-deregistered`

Polls `describe-target-health` every 15 seconds until all targets are in `unused` state. Exits with return code 255 after 40 failed checks.

**Synopsis:**
```bash
aws elbv2 wait target-deregistered \
    --target-group-arn <value> \
    [--targets <value>]
```

---

### 10.5 `wait target-in-service`

Polls `describe-target-health` every 15 seconds until all targets are in `healthy` state. Exits with return code 255 after 40 failed checks.

**Synopsis:**
```bash
aws elbv2 wait target-in-service \
    --target-group-arn <value> \
    [--targets <value>]
```

---
