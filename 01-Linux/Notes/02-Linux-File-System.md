# Part 2 – File Management

---

# **1. mkdir (Make Directory)**

## Definition

The `mkdir` command is used to create one or more new directories (folders).

---

## Why is it Used?

Directories help organize files into logical groups.

Example:

```
CyberLab
│
├── reports
├── notes
├── scripts
└── projects
```

---

## Syntax

```
mkdir directory_name
```

---

## Examples

Create a folder:

```
mkdir reports
```

Create multiple folders:

```
mkdir notes scripts projects
```

Create nested directories:

```
mkdir -p cyberlab/reports/2025
```

---

## Common Options

|Option|Description|
|---|---|
|`-p`|Creates parent directories if they don't exist|
|`-v`|Displays each directory as it is created|

---

## Common Mistakes

❌ Creating a directory that already exists.

Linux displays:

```
mkdir: cannot create directory 'reports': File exists
```

---

## Cybersecurity Use Case

Create folders for:

- Reconnaissance
- Reports
- Exploits
- Logs
- Scripts

to organize penetration testing projects.

---

# **2. touch**

## Definition

Creates an empty file.

If the file already exists, it updates its timestamp.

---

## Syntax

```
touch filename
```

---

## Examples

Create one file:

```
touch notes.txt
```

Create multiple files:

```
touch file1.txt file2.txt report.txt
```

---

## Common Mistake

Many beginners think `touch` writes text into a file.

It only creates an empty file.

---

## Cybersecurity Use Case

Create configuration files or log files before writing scripts.

---

# **3. nano**

## Definition

A simple command-line text editor.

---

## Why Use Nano?

Used to:

- Write scripts
- Edit configuration files
- Take notes
- Modify logs

---

## Syntax

```
nano filename
```

---

## Example

```
nano commands.txt
```

---

## Useful Shortcuts

|Shortcut|Function|
|---|---|
|Ctrl + O|Save file|
|Enter|Confirm filename|
|Ctrl + X|Exit Nano|
|Ctrl + K|Cut line|
|Ctrl + U|Paste line|
|Ctrl + W|Search text|

---

## Cybersecurity Use Case

Edit Bash scripts and configuration files directly on Linux servers.

---

# **4. cat (Concatenate)**

## Definition

Displays the contents of a file.

---

## Syntax

```
cat filename
```

---

## Example

```
cat commands.txt
```

---

## Multiple Files

```
cat file1.txt file2.txt
```

Displays both files.

---

## Creating Files

```
cat > notes.txt
```

Type the content.

Press

```
Ctrl + D
```

to save.

---

## When to Use

Small files.

---

## When NOT to Use

Very large files.

Instead use:

```
less filename
```

---

## Cybersecurity Use Case

Quickly inspect configuration files.

---

# **5. less**

## Definition

Views large files one page at a time.

---

## Syntax

```
less filename
```

---

## Navigation

|Key|Action|
|---|---|
|Space|Next page|
|b|Previous page|
|↑ ↓|Scroll|
|/word|Search|
|q|Quit|

---

## Advantages

Unlike `cat`, it does not print the whole file at once.

Perfect for:

- Logs
- Configuration files
- Large reports

---

## Cybersecurity Use Case

Read log files such as:

```
/var/log/syslog
```

---

# **6. head**

## Definition

Displays the first few lines of a file.

Default:

10 lines.

---

## Syntax

```
head filename
```

---

## Examples

```
head report.txt
```

First five lines:

```
head -5 report.txt
```

---

## Cybersecurity Use Case

Check the beginning of large log files.

---

# **7. tail**

## Definition

Displays the last few lines of a file.

Default:

10 lines.

---

## Syntax

```
tail filename
```

---

## Examples

```
tail report.txt
```

Last five lines:

```
tail -5 report.txt
```

Live monitoring:

```
tail -f logfile.log
```

---

## Cybersecurity Use Case

Monitor logs in real time.

Very common during incident response.

---

# **8. cp (Copy)**

## Definition

Copies files or directories.

The original remains unchanged.

---

## Syntax

```
cp source destination
```

---

## Examples

Copy file:

```
cp report.txt reports/
```

Copy and rename:

```
cp report.txt backup.txt
```

Copy directory:

```
cp -r projects backup_projects
```

---

## Common Options

|Option|Description|
|---|---|
|`-r`|Copy directories recursively|
|`-i`|Ask before overwrite|
|`-v`|Show copied files|

---

## Common Mistakes

Forgetting:

```
-r
```

when copying folders.

---

## Cybersecurity Use Case

Create backups before modifying important files.

---

# **9. mv (Move)**

## Definition

Moves or renames files and directories.

---

## Syntax

```
mv source destination
```

---

## Examples

Rename file:

```
mv report.txt final_report.txt
```

Move file:

```
mv report.txt reports/
```

Move folder:

```
mv scripts cyberlab/
```

---

## Difference Between cp and mv

|cp|mv|
|---|---|
|Copies|Moves|
|Original stays|Original disappears|
|Creates duplicate|Changes location|

---

## Cybersecurity Use Case

Organize evidence into different investigation folders.

---

# **10. rm (Remove)**

## Definition

Deletes files or directories.

---

## Syntax

Delete file:

```
rm filename
```

Delete folder:

```
rm -r folder
```

---

## Common Options

|Option|Description|
|---|---|
|`-r`|Delete directories recursively|
|`-f`|Force deletion|
|`-i`|Ask before deleting|

---

## Warning

Linux does **not** send deleted files to a recycle bin.

Deletion is immediate.

Always verify before pressing Enter.

---

## Cybersecurity Use Case

Remove temporary files after analysis.

---

# **Commands Learned**

```
mkdir
```

Create directories.

---

```
touch
```

Create empty files.

---

```
nano
```

Edit text files.

---

```
cat
```

Display file contents.

---

```
less
```

Read large files page by page.

---

```
head
```

Display first lines.

---

```
tail
```

Display last lines.

---

```
cp
```

Copy files.

---

```
mv
```

Move or rename files.

---

```
rm
```

Delete files.

---

# **Quick Revision**

```
Create Folder
      │
   mkdir
      │
Create File
      │
   touch
      │
Edit File
      │
   nano
      │
Read File
      │
 cat / less
      │
Copy
      │
   cp
      │
Move/Rename
      │
   mv
      │
Delete
      │
   rm
```

---

# **Common Beginner Mistakes (From Our Practice Sessions)**

### Mistake 1

Confusing:

```
cp
```

and

```
mv
```

Remember:

- `cp` → Duplicate
- `mv` → Relocate or Rename

---

### Mistake 2

Trying to copy a directory without:

```
-r
```

---

### Mistake 3

Using:

```
cat
```

for very large files.

Use:

```
less
```

instead.

---

### Mistake 4

Deleting files without checking the path.

Always confirm your location first:

```
pwd
```

---

### Mistake 5 (Our Actual Lab)

While moving files, confusing the **source** and **destination** paths. We debugged this by checking the current directory with `pwd` and listing contents with `ls` before retrying the `mv` command.

---

# **Interview Questions**

1. What is the difference between `mkdir` and `touch`?
2. What is the purpose of the `nano` editor?
3. When should you use `cat` instead of `less`?
4. What is the difference between `head` and `tail`?
5. Explain the difference between `cp` and `mv`.
6. How do you copy a directory?
7. How do you rename a file in Linux?
8. Why is `rm -rf` considered dangerous?
9. What is the purpose of `tail -f`?
10. Explain the difference between copying, moving, and deleting a file.

---

# **Key Takeaways**

- Use `mkdir` to organize your work into directories.
- Use `touch` to create new files quickly.
- Edit files with `nano`.
- Read small files with `cat` and large files with `less`.
- Use `head` and `tail` to inspect the beginning or end of files.
- Remember the difference:
    - `cp` copies.
    - `mv` moves or renames.
    - `rm` permanently deletes.
- Always check your current directory (`pwd`) and contents (`ls`) before moving or deleting files