

````markdown
# Task 05: Create Temporary User with Expiry Date

## Problem

As part of the temporary assignment to the **Nautilus** project,  
a developer named **ravi** requires access for a limited duration.

To ensure smooth access management, a temporary user account  
with an expiry date is needed.

Create a user named **ravi** on **App Server 3** in **Stratos Datacenter**.  
Set the expiry date to **2024-02-17**, ensuring the user is created in lowercase as per standard protocol.

&nbsp;

## Solution

```bash
sudo useradd -e 2024-02-17 ravi
````

 

## Verification

1. **Check user exists and group ID:**

```bash
id ravi
```

2. **Check user details in `/etc/passwd`:**

```bash
grep '^ravi:' /etc/passwd
```

3. **Check account expiry date:**

```bash
sudo chage -l ravi
```

Expected output should include:

```
Account expires    : Feb 17, 2024
```

```

---
