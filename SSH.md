
# 🛠️ Setting Up SSH on RHEL Server

This guide outlines the steps to install, configure, and secure the SSH server on a RHEL (Red Hat Enterprise Linux) system.

---

## 📌 Step 1: Install OpenSSH Server

```bash
sudo dnf install -y openssh-server
```

---

## 📌 Step 2: Enable and Start SSH Service

```bash
sudo systemctl enable sshd
sudo systemctl start sshd
```

---

## ✅ Step 3: Verify SSH Service Status

```bash
sudo systemctl status sshd
```

---

## 🔥 Step 4: Allow SSH in the Firewall (if enabled)

```bash
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload
```

---

## 🔒 Step 5: SSH Server Configuration (Optional)

Edit the SSH configuration file:

```bash
sudo nano /etc/ssh/sshd_config
```

### Common Configuration Options:
- Change port (default is 22):
  ```
  Port 2222
  ```
- Disable root login:
  ```
  PermitRootLogin no
  ```
- Allow only specific users:
  ```
  AllowUsers youruser
  ```

After editing, restart SSH:

```bash
sudo systemctl restart sshd
```

---

## 🔐 Step 6: Set Up Key-Based Authentication (Optional)

1. Generate SSH Key Pair on Client:
   ```bash
   ssh-keygen -t rsa -b 4096
   ```

2. Copy the public key to the RHEL server:
   ```bash
   ssh-copy-id user@rhel-server-ip
   ```

3. Now login without password:
   ```bash
   ssh user@rhel-server-ip
   ```

---

## 🧪 Step 7: Test SSH Connection

```bash
ssh user@rhel-server-ip
```

If you changed the port:
```bash
ssh -p 2222 user@rhel-server-ip
```

---

## 🚫 Optional: Disable Password Authentication (More Secure)

Edit `/etc/ssh/sshd_config`:
```
PasswordAuthentication no
```

Then restart the SSH service:

```bash
sudo systemctl restart sshd
```

---

## ✅ Done!

Your RHEL server is now configured for secure SSH access.

---
