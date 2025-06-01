# Task 07: Disable Root SSH Login

---

## Problem

Following security audits, the **xFusionCorp Industries** security team has rolled out new protocols,  
including the restriction of direct root SSH login.

Your task is to disable direct SSH root login on all app servers within the **Stratos Datacenter**.

---

## Solution

1️⃣ Open the SSH configuration file for editing:
```bash
sudo vi /etc/ssh/sshd_config
````

2️⃣ Locate the line:

```
PermitRootLogin yes
```

and change it to:

```
PermitRootLogin no
```

3️⃣ Save the file and exit (press `Esc`, then type `:wq` and press Enter).

4️⃣ Restart the SSH service to apply changes:

```bash
sudo systemctl restart sshd
```

---

## Verification

✅ Confirm the setting in the SSH configuration file:

```bash
grep '^PermitRootLogin' /etc/ssh/sshd_config
```

Expected output:

```
PermitRootLogin no
```

✅ Test SSH login as root (should be denied):

```bash
ssh root@<server-ip>
```

You should receive a **"Permission denied"** message.
