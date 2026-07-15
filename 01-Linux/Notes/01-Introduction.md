Linux Basics & Navigation**

---

# **1. What is Linux?**

## Definition

Linux is a free and open-source operating system based on the Linux Kernel. It acts as a bridge between the computer hardware and the software running on it.

An operating system manages hardware resources such as CPU, memory, storage, files, users, and applications.

---

## Why is Linux Important?

Linux powers:

- Most web servers
- Cloud platforms (AWS, Azure, Google Cloud)
- Android phones (Linux Kernel)
- Supercomputers
- IoT devices
- Cybersecurity tools like Kali Linux and Parrot OS

More than 90% of the world's servers run Linux because it is stable, secure, customizable, and lightweight.

---

## Advantages of Linux

- Free and Open Source
- Secure and Stable
- Fast Performance
- Multi-user Support
- Strong Permission System
- Highly Customizable
- Excellent for Programming and Cybersecurity

---

## Linux Distributions (Distros)

A Linux distribution combines the Linux Kernel with software, package managers, and desktop environments.

Common distributions include:

- Ubuntu (Beginner Friendly)
- Kali Linux (Penetration Testing)
- Debian (Stable Servers)
- Fedora (Latest Features)
- Arch Linux (Advanced Users)
- Red Hat Enterprise Linux (Enterprise)

---

## Cybersecurity Use Case

Most penetration testing tools such as Nmap, Metasploit, Burp Suite, and Wireshark run natively on Linux.

---

# **2. Linux File System**

Unlike Windows, Linux does **not** use drives like **C:** or **D:**.

Everything starts from a single root directory.

```
/
├── home
│   └── soham
│       ├── Documents
│       ├── Downloads
│       └── cyberlab
│
├── etc
├── var
├── usr
├── bin
├── root
├── tmp
└── opt
```

---

## Important Directories

### `/`

Root directory.

The top-most directory from which every other directory starts.

---

### `/home`

Stores personal folders of all users.

Example:

```
/home/soham
```

---

### `/root`

Home directory of the **root** user.

Do not confuse this with `/`.

```
/
/root
```

are completely different.

---

### `/etc`

Contains system configuration files.

Examples:

- Network configuration
- User accounts
- DNS configuration

---

### `/var`

Stores logs, cache, temporary server files.

Cybersecurity professionals often investigate:

```
/var/log
```

---

### `/bin`

Contains essential Linux commands.

Examples:

```
ls

cp

mv

cat
```

---

### `/usr`

Contains installed software and applications.

---

### `/tmp`

Stores temporary files.

Files here may be deleted automatically.

---

# **3. Absolute vs Relative Paths**

## Absolute Path

Starts from the root directory (`/`).

Example:

```
/home/soham/cyberlab/notes
```

An absolute path always points to the same location regardless of your current directory.

---

## Relative Path

Starts from your current working directory.

Example:

```
notes/

../reports

scripts/
```

Relative paths depend on where you currently are.

---

## Example

Current directory:

```
/home/soham/cyberlab
```

Absolute path:

```
/home/soham/cyberlab/reports
```

Relative path:

```
reports
```

---

# **4. Important Linux Symbols**

---

## `/`

Represents the root directory.

Example:

```
cd /
```

Moves to the root of the file system.

---

## `~`

Represents the current user's home directory.

Example:

```
cd ~
```

Returns to:

```
/home/soham
```

---

## `.`

Represents the current directory.

Example:

```
find . -name "*.txt"
```

Searches from the current directory.

---

## `..`

Represents the parent directory.

Example:

```
cd ..
```

Moves one level up.

---

## `*`

Wildcard character.

Matches any number of characters.

Examples:

```
find . -name "*.txt"
```

Find every `.txt` file.

```
find . -name "report*"
```

Matches:

```
report.txt

report1.pdf

reports.docx
```

```
find . -name "*report*"
```

Matches every filename containing the word "report".

---

## `|` (Pipe)

Passes the output of one command as input to another.

Example:

```
history | grep chmod
```

Searches your command history for commands containing `chmod`.

---

# **5. pwd (Print Working Directory)**

## Definition

Displays the absolute path of the current working directory.

---

## Why is it Used?

Before creating, deleting, or modifying files, you should verify your current location.

---

## Syntax

```
pwd
```

---

## Example

```
pwd
```

Output

```
/home/soham/cyberlab
```

---

## Common Mistake

❌ Thinking `pwd` lists files.

It only displays the current directory path.

---

## Cybersecurity Use Case

Always verify your location before editing configuration files on a Linux server.

---

# **6. ls (List Directory Contents)**

## Definition

Displays files and folders inside a directory.

---

## Syntax

```
ls
```

---

## Common Options

|Option|Description|
|---|---|
|`ls`|List directory contents|
|`ls -l`|Long listing with permissions, owner, size, and date|
|`ls -a`|Show hidden files|
|`ls -lh`|Human-readable file sizes|
|`ls -lt`|Sort by modification time|
|`ls -lr`|Reverse sorting order|
|`ls -R`|Recursive listing|
|`ls -1`|One file/folder per line|

---

## Example

```
ls
```

Output

```
notes
reports
scripts
projects
```

---

## Hidden Files

Files beginning with a dot (`.`) are hidden.

Example:

```
.secret_key.txt
```

Use:

```
ls -a
```

to display hidden files.

---

## Cybersecurity Use Case

Hidden files often contain configuration data or sensitive information that attackers and defenders both investigate.

---

# **7. cd (Change Directory)**

## Definition

Changes the current working directory.

---

## Syntax

```
cd directory_name
```

---

## Common Commands

|Command|Description|
|---|---|
|`cd`|Go to home directory|
|`cd ~`|Go to home directory|
|`cd ..`|Move one level up|
|`cd ../..`|Move two levels up|
|`cd -`|Return to previous directory|
|`cd /`|Go to root directory|
|`cd folder_name`|Enter a directory|

---

## Examples

Go to home:

```
cd
```

Go to parent directory:

```
cd ..
```

Go to root:

```
cd /
```

Return to previous directory:

```
cd -
```

---

## Common Mistakes

❌ Forgetting spaces.

Incorrect:

```
cd..
```

Correct:

```
cd ..
```

---

## Cybersecurity Use Case

During incident response or penetration testing, analysts frequently move between directories containing logs, scripts, and evidence.

---

# **Commands Learned**

```
pwd
```

Displays the current working directory.

---

```
ls
```

Lists directory contents.

---

```
ls -l
```

Displays permissions, owner, size, and date.

---

```
ls -a
```

Displays hidden files.

---

```
cd
```

Moves to the home directory.

---

```
cd ..
```

Moves one directory up.

---

```
cd /
```

Moves to the root directory.

---

```
cd -
```

Returns to the previous directory.

---

# **Quick Revision**

```
Linux
│
├── File System
│
├── Root Directory (/)
│
├── Home Directory (~)
│
├── Absolute Path
│
├── Relative Path
│
├── pwd
│
├── ls
│
└── cd
```

---

# **Common Beginner Mistakes (From Our Practice Sessions)**

### Mistake 1

Using:

```
ls-1
```

Correct:

```
ls -1
```

---

### Mistake 2

Confusing:

```
cd /
```

with

```
cd ~
```

Remember:

- `/` → Root directory
- `~` → Home directory

---

### Mistake 3

Thinking:

```
pwd
```

lists files.

It only prints the current directory path.

---

### Mistake 4

Using relative and absolute paths interchangeably without checking the current directory.

Always verify your location first:

```
pwd
```

---

# **Interview Questions**

1. What is Linux?
2. What is the Linux Kernel?
3. Why is Linux preferred for servers and cybersecurity?
4. What is the difference between Linux and Windows?
5. Explain the Linux file system hierarchy.
6. What is the difference between an absolute path and a relative path?
7. What is the purpose of the `pwd` command?
8. What is the difference between `pwd` and `ls`?
9. Explain the most common `ls` options.
10. What is the difference between `cd /`, `cd ~`, `cd ..`, and `cd -`?
11. What are hidden files, and how can you view them?
12. Explain the purpose of `.`, `..`, `~`, `*`, and `|` in Linux.

---

# **Key Takeaways**

- Linux uses a **single hierarchical file system** beginning at the root (`/`).
- Always verify your current location using `pwd`.
- Use `ls` to inspect directory contents before making changes.
- Understand the difference between **absolute** and **relative** paths.
- Learn the meaning of important symbols (`.`, `..`, `~`, `/`, `*`, `|`)—they appear constantly in Linux and cybersecurity.
- Mastering navigation commands is the foundation for every other Linux operation