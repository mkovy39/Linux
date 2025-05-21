# Task 03: Create Non-Interactive User

---

## Problem

To accommodate the backup agent tool's specifications,  
the system admin team at **xFusionCorp Industries** requires the creation of a user with a non-interactive shell.

Create a user named **siva** with a non-interactive shell on **App Server 3**.

---

## Solution

```bash
sudo useradd -s /sbin/nologin siva
````

---

## Verification

**Check user shell in `/etc/passwd`:**

```bash
cat /etc/passwd | grep 'siva'
```

