
# User and Group Management with Permissions on RHEL


## Step 1: Create Users

Create four users: `user1`, `user2`, `acc1`, `acc2`.

```bash
 useradd user1
 useradd user2
 useradd acc1
 auseradd acc2
```

---

## 👪 Step 2: Create Groups

Create two groups: `students` and `office`.

```bash
 groupadd students
 groupadd office
```

---

## ➕ Step 3: Add Users to Groups

Add `user1` and `user2` to the `students` group:

```bash
 usermod -aG students user1
 usermod -aG students user2
```

Add `acc1` and `acc2` to the `office` group:

```bash
 usermod -aG office acc1
 usermod -aG office acc2
```

To verify 
```bash
id user1
id acc1
```

---

## 📁 Step 4: Create Group Directories

Create directories for each group:

```bash
 mkdir /students
 mkdir /office
```

Check Existing Permision and Ownership
```bash
ls -l
```

---

## 🔐 Step 5: Assign Group Ownership

Assign group ownership of each directory:

```bash
 chown :students /students
 chown :office /office
```

Check Ownership
```bash
ls -l
```

---

## ✏️ Step 6: Set Directory Permissions

Give read/write/execute access to group members only:

```bash
 chmod 770 /students
 chmod 770 /office
```

This means:
- Owner: full access
- Group: full access
- Others: no access

---

## 📌 Step 7: Set Sticky Bit (optional)

Set the **sticky bit** to prevent users from deleting each other’s files within the shared directory.

```bash
 chmod +t /students
 chmod +t /office
```

Now only file **owners** and **root** can delete files inside those directories.

---

## 🧪 Step 8: Verify Permissions

```bash
ls -ld /students /office
```

Expected output:
```
drwxrwx--T 2 root students 4096 ... /students
drwxrwx--T 2 root office   4096 ... /office
```

---

## ✅ Summary

| Task                         | Command Example                        |
|------------------------------|-----------------------------------------|
| Create users                 | `adduser user1`                         |
| Create groups                | `groupadd students`                    |
| Add user to group            | `usermod -aG students user1`           |
| Create folder                | `mkdir /students`                      |
| Change group ownership       | `chown :students /students`            |
| Set permissions              | `chmod 770 /students`                  |
| Set sticky bit               | `chmod +t /students`                   |

---
