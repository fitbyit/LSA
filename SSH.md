
# 🛠️ Setting Up SSH on RHEL Server

---

## 📌 Step 1: Install OpenSSH Server if not 

```bash
yum install -y openssh-server
```

---

## ✅ Step 2: Verify SSH Service Status

```bash
service sshd status
```

> if not running then start the service
```bash
service sshd start
```

---

## 🔥 Step 3: Allow SSH in the Firewall (if enabled)

```bash
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload
```

---

## 🔒 Step 4: SSH Server Configuration

Edit the SSH configuration file:

```bash
gedit /etc/ssh/sshd_config
```

### Common Configuration Options:
- Disable root login:
  ```
  PermitRootLogin no
  ```
- Allow only specific users:
  ```
  AllowUsers username
  ```
- Password Authentication
  ```
  PasswordAuthentication yes
  ``` 

After editing, restart SSH:

```bash
service sshd restart
```

## 🔐 Step 5: Check IP address
```bash
ifconfig
```
> Note Down your server ip address

## 🔐 Step 6: On Client Machine (Windows) on CMD 
```
ssh username@serverip
```
> enter password for the spcified user


---

## 🔐 To Setup Key-Based Authentication

1. Generate SSH Key Pair on Client:
   ```bash
   ssh-keygen -t rsa
   ```
  
  > press enter to store in default location and enter passphrase to genreate private key
  
  > Note : Remember Passphrase as it will be used to verify your private key while connecting

2. Copy the public key to the RHEL server:

> if clinet if linux machine 

   ```bash
   ssh-copy-id user@rhel-server-ip
   ```

> if client is windows machine : Open cmd on .ssh path
  
  ```
  scp id_rsa.pub user@rhel-server-ip:~/.ssh/authorized_keys
  ```
  
3. Edit sshd_config
  Edit `/etc/ssh/sshd_config`:
  ```
  PasswordAuthentication no
  ```
  Then restart the SSH service:
  
  ```bash
  service sshd restart
  ```

5. Now login without password using client machine:

   ```bash
   ssh user@rhel-server-ip
   ```
   > `Note:` Can Ask to enter passphrase to verify client's private key

---


## ✅ Done!

Your RHEL server is now configured for secure SSH access.

---
