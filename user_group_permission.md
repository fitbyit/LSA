
# 👥 User Management, Group Management, and Permissions on RHEL

This document provides a guide for managing users, groups, and file permissions on a RHEL (Red Hat Enterprise Linux) system.

---

## 👤 User Management

### ✅ Add a New User
```bash
sudo adduser username
```

### 🔑 Set Password for User
```bash
sudo passwd username
```

### ❌ Delete a User
```bash
sudo userdel username
```

To remove user home directory as well:
```bash
sudo userdel -r username
```

### ✏️ Modify User
```bash
sudo usermod -aG groupname username
```

---

## 👪 Group Management

### ✅ Add a New Group
```bash
sudo groupadd groupname
```

### ✏️ Add User to Group
```bash
sudo usermod -aG groupname username
```

### ❌ Delete a Group
```bash
sudo groupdel groupname
```

### 🔍 View User Groups
```bash
groups username
```

---

## 🔐 File and Directory Permissions

### 📄 Permission Types

| Symbol | Meaning         |
|--------|------------------|
| r      | Read             |
| w      | Write            |
| x      | Execute          |
| -      | No permission    |

### 👥 Ownership Structure
```bash
-rwxr-xr-- 1 owner group filename
```

- Owner: `rwx`
- Group: `r-x`
- Others: `r--`

---

### 🔄 Change Ownership
```bash
sudo chown newowner:newgroup filename
```

---

### ✏️ Change Permissions

#### Numeric Format
```bash
chmod 755 filename
```

| Number | Permission |
|--------|------------|
| 7      | rwx        |
| 6      | rw-        |
| 5      | r-x        |
| 4      | r--        |
| 3      | -wx        |
| 2      | -w-        |
| 1      | --x        |
| 0      | ---        |

#### Symbolic Format
```bash
chmod u+x filename
chmod g-w filename
chmod o=r filename
```

---

## 🧪 Check File Permissions
```bash
ls -l filename
```

---

## ✅ Summary

- Use `adduser`, `userdel`, `usermod` for user management.
- Use `groupadd`, `groupdel`, `usermod` for group management.
- Use `chmod`, `chown`, `ls -l` for permission handling.

---
