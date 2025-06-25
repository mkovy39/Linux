
# SSH Basics and Passwordless Authentication

## 1. What is SSH?

**SSH (Secure Shell)** is a cryptographic network protocol used for securely accessing and managing remote servers. It encrypts data transferred between the client and the server, ensuring confidentiality and integrity over unsecured networks.

---

## 2. How SSH Works

SSH uses a **client-server** model and typically operates on **TCP port 22**. Here's how it works:

- The **SSH client** initiates a connection to the server.
- The **server responds** with its public host key.
- If the client trusts the host, it proceeds to authentication:
  - Either by **username and password**, or
  - More securely via **key-based authentication**.
- Once authenticated, the client and server communicate through an **encrypted channel**.

---

## 3. How to Configure Passwordless SSH Authentication

### Step 1: Generate SSH Key Pair (on your local machine)

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
````

This creates:

* `~/.ssh/id_rsa` (private key)
* `~/.ssh/id_rsa.pub` (public key)

> **Note:** Never share your private key.

---

### Step 2: Copy Public Key to the Remote Server

Use `ssh-copy-id`:

```bash
ssh-copy-id user@server_ip
```

Or manually:

```bash
cat ~/.ssh/id_rsa.pub | ssh user@server_ip "mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys"
```

---

### Step 3: Test Passwordless SSH

```bash
ssh user@server_ip
```

If everything is configured correctly, no password will be required.

---

## 4. How to Name the Server Locally in SSH Config (and Why)

### Purpose:

To simplify connections using a **friendly alias** instead of repeatedly typing the full command with IP, username, and key path.

### Step 1: Open SSH config

```bash
nano ~/.ssh/config
```

### Step 2: Add an Entry

```ssh
Host sandbox
    HostName 192.168.22.149
    User ovy
    IdentityFile ~/.ssh/id_rsa
```

### Step 3: Connect with Alias

```bash
ssh sandbox
```

---

## 5. How to Name the Server via `/etc/hosts`

### Purpose:

To associate a **custom name with an IP address** system-wide on your local machine.

### Step 1: Edit Hosts File

```bash
sudo nano /etc/hosts
```

### Step 2: Add Entry

```
192.168.22.149   sandbox.local
```

### Step 3: Connect Using New Hostname

```bash
ssh ovy@sandbox.local
```

---

### Summary

| Task                          | Method                      |
| ----------------------------- | --------------------------- |
| Passwordless SSH              | `ssh-keygen`, `ssh-copy-id` |
| Friendly alias for SSH        | `~/.ssh/config`             |
| System-wide hostname shortcut | `/etc/hosts`                |

---

> Created for documentation and practice.
> Author: Md. Khiruzzaman
> Date: 2025
