# Task 01: Create User with Custom UID and Home Directory

---

## Problem

Create a user named **john** on **App Server 2** within the **Stratos Datacenter**.  
Assign a unique UID `1655` and designate the home directory as `/var/www/john`.

---

## Solution

```bash
sudo useradd -u 1655 -d /var/www/john -m john
````

---

## Verification

**Check user entry in `/etc/passwd`:**

```bash
cat /etc/passwd | grep 'john'
```

```

