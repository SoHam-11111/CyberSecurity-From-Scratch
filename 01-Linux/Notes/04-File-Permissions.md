# **Part 4 – Users & Permissions**

---

# **1. Multi-User System**

## Definition

Linux is a **multi-user operating system**, meaning multiple users can use the same computer while keeping their files and permissions separate.

Each user has:

- Home directory
- Username
- Password
- Permissions
- Groups

---

## Why Does Linux Have Multiple Users?

Different users perform different tasks.

Example:

|User|Role|
|---|---|
|Root|Full system control|
|Admin|Manage users and software|
|Developer|Write code|
|Guest|Limited access|

This improves:

- Security
- Privacy
- System Stability

---

## Cybersecurity Use Case

Attackers who gain access to a normal user account **do not automatically gain administrator privileges**.

---

# **2. whoami**

## Definition

Displays the username of the currently logged-in user.

---

## Syntax

```
whoami
```

---

## Example

```
whoami
```

Output

```
soham
```

---

## Why Use It?

Useful to verify:

- Which account you're using.
- Whether you are logged in as **root** or a normal user.

---

## Cybersecurity Use Case

Before running powerful commands, verify that you are not accidentally logged in as **root**.

---

# **3. id**

## Definition

Displays detailed information about the current user.

---

## Syntax

```
id
```

---

## Example

```
id
```

Output

```
uid=1000(soham)
gid=1000(soham)
groups=1000(soham),27(sudo),1001(docker)
```

---

## Understanding the Output

### UID

User ID

Example:

```
uid=1000
```

Unique number assigned to a user.

---

### GID

Group ID

Example:

```
gid=1000
```

Represents the user's primary group.

---

### Groups

Additional groups the user belongs to.

Example:

```
sudo
docker
adm
```

These determine additional permissions.

---

## Cybersecurity Use Case

Quickly determine whether a user has administrative privileges.

---

# **4. Root User**

## Definition

The **root** user is the administrator of Linux.

Root has unrestricted access to the system.

---

## Capabilities

Root can:

- Install software
- Delete any file
- Modify system configuration
- Add or remove users
- Shut down the system
- Change permissions

---

## Why Not Use Root All the Time?

If malware infects a root session,

the attacker also gains full control.

Always use a normal account unless administrator privileges are required.

---

## Our Practice

You switched to root using:

```
sudo su
```

Then verified using:

```
whoami
```

Output

```
root
```

---

# **5. sudo**

## Definition

Allows a normal user to temporarily execute commands as another user (usually root).

---

## Syntax

```
sudo command
```

---

## Example

```
sudo apt update
```

---

## Why Use sudo?

Instead of staying logged in as root,

Linux grants administrator privileges **only for a single command**.

This reduces security risks.

---

## Cybersecurity Use Case

Always use **sudo only when necessary**.

Avoid browsing or daily work as the root user.

---

# **6. Linux Permissions**

Every file and directory has permissions.

Example

```
-rw-r--r--
```

or

```
drwxr-xr-x
```

---

## Structure

```
-rw-r--r--
```

Breakdown

```
-

rw-

r--

r--
```

---

### First Character

|Symbol|Meaning|
|---|---|
|`-`|File|
|`d`|Directory|

---

### Remaining Nine Characters

Three groups:

```
Owner

Group

Others
```

Each group has

```
r

w

x
```

---

## Permission Meaning

|Symbol|Meaning|
|---|---|
|r|Read|
|w|Write|
|x|Execute|

---

Example

```
rw-
```

means

- Read ✅
- Write ✅
- Execute ❌

---

# **7. chmod**

## Definition

Changes file or directory permissions.

---

## Syntax

```
chmod permissions filename
```

---

## Symbolic Mode

Add write permission

```
chmod u+w file.txt
```

---

Remove execute permission

```
chmod u-x file.txt
```

---

Add write permission to others

```
chmod o+w file.txt
```

---

Add write permission to group

```
chmod g+w file.txt
```

---

Our Practice

You ran

```
chmod o+w commands.txt

chmod g+w commands.txt
```

Permissions became

```
-rw-rw-rw-
```

Everyone now had

Read

Write

No Execute

---

# **8. Numeric Permissions**

Each permission has a value.

|Permission|Value|
|---|---|
|Read|4|
|Write|2|
|Execute|1|

Add the values together.

---

## Examples

### 7

```
4+2+1
```

Read

Write

Execute

---

### 6

```
4+2
```

Read

Write

---

### 5

```
4+1
```

Read

Execute

---

### 4

```
4
```

Read Only

---

### 0

No permissions.

---

# **Common Permission Values**

---

## 777

```
rwx

rwx

rwx
```

Everyone has full control.

⚠️ Very insecure.

---

## 755

```
Owner

rwx

Group

r-x

Others

r-x
```

Common for:

Programs

Directories

Web servers

---

## 700

```
Owner

rwx

Group

---

Others

---
```

Only the owner has access.

Very secure.

---

## 644

```
Owner

rw-

Group

r--

Others

r--
```

Most common permission for text files.

---

## 600

```
Owner

rw-

Group

---

Others

---
```

Used for

SSH Keys

Passwords

Sensitive files

---

# **Why 600 is Better Than 777**

During practice you answered:

> 600 is more secure because only the owner can read and modify the file.

Exactly.

Example

```
Private SSH Key
```

Should **never** have

```
777
```

permissions.

---

# **Symbolic vs Numeric**

|Symbolic|Numeric|
|---|---|
|u+x|chmod 755|
|g-w|chmod 740|
|o-r|chmod 600|

Both methods change permissions.

---

# **Commands Learned**

```
whoami
```

Display current user.

---

```
id
```

Display UID, GID, and groups.

---

```
sudo
```

Run commands with administrator privileges.

---

```
chmod
```

Modify file permissions.

---

```
ls -l
```

View file permissions.

---

# **Quick Revision**

```
Users
      │
      ▼
whoami
      │
      ▼
id
      │
      ▼
Root
      │
      ▼
sudo
      │
      ▼
Permissions
      │
      ▼
chmod
```

---

# **Common Beginner Mistakes (From Our Practice Sessions)**

### Mistake 1

Thinking

```
d
```

means "disk."

It actually means **Directory**.

---

### Mistake 2

Confusing

```
/root
```

with

```
/
```

Remember:

- `/` → Root of the filesystem
- `/root` → Home directory of the root user

---

### Mistake 3

Staying logged in as root for everyday work.

Best practice:

Use a normal user and only use:

```
sudo
```

when required.

---

### Mistake 4

Giving unnecessary permissions.

Avoid:

```
chmod 777
```

unless absolutely necessary.

Use the principle of **least privilege**.

---

### Mistake 5 (Our Actual Practice)

You accidentally added write permissions to **Group** and **Others** using:

```
chmod g+w
chmod o+w
```

This was a great exercise because it showed how permissions change and why granting extra access should be done carefully.

---

# **Interview Questions**

1. What is a multi-user operating system?
2. What does the `whoami` command do?
3. Explain the output of the `id` command.
4. Who is the root user?
5. Why is using `sudo` safer than logging in as root?
6. Explain Linux file permissions.
7. What do `r`, `w`, and `x` represent?
8. What is the difference between a file (`-`) and a directory (`d`) in `ls -l` output?
9. Explain the difference between symbolic and numeric permissions.
10. What do `777`, `755`, `700`, `644`, and `600` mean?
11. Why is `600` recommended for sensitive files such as SSH keys?

---

# **Key Takeaways**

- Linux is designed as a **multi-user operating system**, with users and groups controlling access.
- Use `whoami` and `id` to identify the current user and their privileges.
- The **root** user has unrestricted access, so use it only when necessary.
- Prefer `sudo` over logging in as root to reduce security risks.
- File permissions are divided into **Owner**, **Group**, and **Others**, with **Read (r)**, **Write (w)**, and **Execute (x)** permissions.
- Learn both **symbolic** (`u+w`) and **numeric** (`755`, `644`, `600`) permission formats.
- Follow the **Principle of Least Privilege**: grant only the permissions that are actually required.
