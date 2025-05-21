# Task 02: Create Group and Add User

---

## Problem

Create a group named **nautilus_noc** across all App servers within the **Stratos Datacenter**.  
Add the user **stark** into the `nautilus_noc` group.  
If the user doesn't exist, create it as well.

---

## Solution

```bash
sudo groupadd nautilus_noc
sudo useradd -g nautilus_noc stark
````

---

## Verification

**1. Check group creation:**

```bash
getent group nautilus_noc
```

**2. Check user group membership:**

```bash
groups stark
```

```
