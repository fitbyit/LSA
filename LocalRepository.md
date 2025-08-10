## ✅ Setup Custom Local Repository on RHEL using RHEL DVD  

---

### 🥇 1. Attach ISO (or insert DVD)

If you're using a virtual machine:

* Attach the RHEL ISO to the virtual DVD drive.
<img width="350" alt="image" src="https://github.com/user-attachments/assets/182d8f68-d844-48a3-a526-71b36e8c385c" />


---

### 🧭 2. Find the mount path using `lsblk`

Run:

```bash
lsblk
```

Example output:

```
sr0     11:0    1  11.9G  0 rom  /run/media/admin/RHEL-9-6-0-BaseOS-x86_64
```

📌 This tells you the ISO is auto-mounted at:

```
/run/media/admin/RHEL-9-6-0-BaseOS-x86_64
```

✅ Check contents:

```bash
ls /run/media/admin/RHEL-9-6-0-BaseOS-x86_64
```

You should see:

```
AppStream  BaseOS  RPM-GPG-KEY-redhat-release  ...
```

---

### 📁 3. Create `/myrepo` and copy contents

Create your target directory:

```bash
sudo mkdir -p /myrepo
```

Copy `AppStream` and `BaseOS` directories **with their metadata**:

```bash
cd /run/media/admin/RHEL-9-6-0-BaseOS-x86_64/
cp -rv BaseOS/ /myrepo
cp -rv AppStream/ /myrepo
```

### 📝 4. Create local repo config (`myrepo.repo`)

Create a single `.repo` file pointing to both `BaseOS` and `AppStream`.

```bash
gedit /etc/yum.repos.d/myrepo.repo
```
Add Configuration as below in `myrepo.repo` file :
```bash
[myrepo-baseos]
name=RHEL 9 - BaseOS (Local)
baseurl=file:///myrepo/BaseOS/
enabled=1
gpgcheck=0

[myrepo-appstream]
name=RHEL 9 - AppStream (Local)
baseurl=file:///myrepo/AppStream/
enabled=1
gpgcheck=0
```

---


---

### 🔍 5. List all enabled repositories

```bash
yum repolist
```
---

### 📦 7. Install a package or check for updates

#### Example: Install `dhcp-server`

```bash
yum install dhcp-server
```

#### Check for available updates:

```bash
yum check-update
```

---

## ✅ Summary Table

| Step                    | Command / Description                                                            |
| ----------------------- | -------------------------------------------------------------------------------- |
| Attach ISO              | Mounts automatically at `/run/media/<user>/<label>`                              |
| Find mount path         | `lsblk` → look for `/dev/sr0`                                                    |
| Copy repo content       | `cp -av BaseOS AppStream /myrepo/`                                               |
| Create repo file        | Add `[myrepo-baseos]` and `[myrepo-appstream]` in `/etc/yum.repos.d/myrepo.repo` |
| Verify enabled repos    | `yum repolist`                                                                   |
| Install or update       | `yum install <package>` or `yum update`                                          |

---
