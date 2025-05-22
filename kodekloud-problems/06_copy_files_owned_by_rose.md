
# Task 06: Copy Files Owned by Specific User While Preserving Directory Structure

---

## Problem

Due to an accidental data mix-up, user data was unintentionally mingled on **Nautilus App Server 3**  
at the `/home/usersdata` location by the Nautilus production support team in **Stratos DC**.

To rectify this, specific user data needs to be filtered and relocated.

---

## Objective

Locate all **files** (excluding directories) owned by user **rose** within the `/home/usersdata` directory  
on **App Server 3**, and **copy them** (preserving the directory structure) to the `/ecommerce` directory.

---

## Solution

```bash
find /home/usersdata -type f -user rose -exec cp --parents {} /ecommerce \;
````

---

## Verification

**1. List files copied into `/ecommerce`:**

```bash
find /ecommerce -type f
```

**2. Confirm file ownership (optional):**

```bash
find /ecommerce -type f -user rose
```
