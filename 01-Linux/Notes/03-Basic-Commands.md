# **Part 3 – Searching & Text Processing**

---

# **1. find**

## Definition

The `find` command is used to search for files and directories within a directory hierarchy.

Unlike `ls`, which only lists the contents of the current directory, `find` searches recursively through all subdirectories.

---

## Why is it Used?

Finding files manually in large systems is difficult. `find` helps locate files quickly based on:

- Name
- File type
- Size
- Date
- Permissions
- Owner

---

## Syntax

```
find <starting_directory> [options]
```

---

## Examples

Search for a file:

```
find . -name "report.txt"
```

`.` means search from the current directory.

---

Search from home directory:

```
find ~/cyberlab -name "commands.txt"
```

---

Search for directories:

```
find . -type d
```

---

Search only files:

```
find . -type f
```

---

## Common Options

|Option|Description|
|---|---|
|`.`|Search current directory|
|`-name`|Search by exact filename|
|`-type f`|Search only files|
|`-type d`|Search only directories|
|`-iname`|Ignore case while searching|

---

## Cybersecurity Use Case

Locate:

- Log files
- Password files
- Configuration files
- Malware samples
- Scripts

Example:

```
find /var/log -name "*.log"
```

---

# **2. Wildcards (*)**

## Definition

A wildcard is a special character used to match multiple filenames.

The most common wildcard is:

```
*
```

which means

> **Match any number of characters.**

---

## Examples

### Find all text files

```
find . -name "*.txt"
```

Matches

```
notes.txt
report.txt
commands.txt
```

---

### Starts with "report"

```
find . -name "report*"
```

Matches

```
report.txt
report.pdf
report_backup.doc
```

---

### Ends with "report"

```
find . -name "*report"
```

Matches

```
finalreport
myreport
```

---

### Contains "report"

```
find . -name "*report*"
```

Matches

```
report.txt
myreport.pdf
report_backup.doc
```

---

## Common Mistake

Thinking

```
*
```

means "everything."

Actually it means

> Match **any characters**.

---

# **3. grep (Global Regular Expression Print)**

## Definition

Searches for specific text or patterns inside files.

Unlike `find`, which searches for files,

`grep` searches **inside files**.

---

## Syntax

```
grep "text" filename
```

---

## Example

```
grep "server" logfile.txt
```

Displays every line containing:

```
server
```

---

## Difference Between find and grep

|find|grep|
|---|---|
|Searches files|Searches text inside files|
|Looks at filenames|Looks at file contents|

---

## Cybersecurity Use Case

Search log files for:

- Failed logins
- Errors
- Suspicious activity
- Usernames
- IP addresses

---

# **4. grep -i**

## Definition

Performs a case-insensitive search.

---

## Example

```
grep -i "server" logfile.txt
```

Matches

```
Server
SERVER
server
SeRvEr
```

---

## Why Use It?

Useful when capitalization is unknown.

---

# **5. grep -n**

## Definition

Displays the line number where the match occurs.

---

## Example

```
grep -n "admin" users.txt
```

Output

```
12:admin
```

Means

Line 12 contains

```
admin
```

---

# **6. grep -c**

## Definition

Counts how many lines contain the matching text.

---

## Example

```
grep -c "error" logfile.txt
```

Output

```
17
```

Meaning

17 lines contain the word

```
error
```

---

# **7. Pipes ( | )**

## Definition

A pipe sends the output of one command directly into another command.

Instead of saving output into a file, it is immediately passed to the next command.

---

## Syntax

```
command1 | command2
```

---

## Example

```
history | grep chmod
```

Step 1

```
history
```

produces hundreds of commands.

↓

Step 2

```
grep chmod
```

shows only commands containing:

```
chmod
```

---

## More Examples

Find text then count it.

```
grep "error" logfile.txt | wc -l
```

---

List files then search.

```
ls | grep report
```

---

## Why Use Pipes?

Allows Linux commands to work together.

Think of them as connecting building blocks.

---

# **8. head**

## Definition

Displays the first 10 lines of a file by default.

---

## Syntax

```
head filename
```

---

## Example

```
head report.txt
```

---

Specify lines

```
head -5 report.txt
```

---

## Cybersecurity Use Case

Read the beginning of configuration files or logs.

---

# **9. tail**

## Definition

Displays the last 10 lines of a file by default.

---

## Syntax

```
tail filename
```

---

## Example

```
tail report.txt
```

---

Real-time monitoring

```
tail -f logfile.log
```

This updates continuously as new log entries are added.

Very common for monitoring servers.

---

# **10. wc (Word Count)**

## Definition

Counts lines, words, and characters in a file.

---

## Syntax

```
wc filename
```

---

## Common Options

|Command|Description|
|---|---|
|`wc -l`|Count lines|
|`wc -w`|Count words|
|`wc -c`|Count characters|

---

## Examples

Count lines

```
wc -l report.txt
```

---

Count words

```
wc -w report.txt
```

---

Count characters

```
wc -c report.txt
```

---

## Cybersecurity Use Case

Count:

- Log entries
- User accounts
- Passwords
- Alerts

---

# **11. history**

## Definition

Displays previously executed commands.

Linux stores command history for easier reuse.

---

## Syntax

```
history
```

---

## Example

```
history
```

Output

```
1 pwd
2 ls
3 mkdir reports
4 nano notes.txt
```

---

## Useful Commands

Search history

```
history | grep nano
```

Repeat previous command

```
!!
```

---

Reverse Search

Press

```
Ctrl + R
```

Type part of a previous command.

Linux automatically searches command history.

---

## Cybersecurity Use Case

Review commands executed during troubleshooting or investigations.

---

# **Commands Learned**

```
find
```

Search for files and directories.

---

```
grep
```

Search text inside files.

---

```
grep -i
```

Ignore case.

---

```
grep -n
```

Show line numbers.

---

```
grep -c
```

Count matching lines.

---

```
head
```

Show first lines.

---

```
tail
```

Show last lines.

---

```
wc
```

Count lines, words, characters.

---

```
history
```

Display previously executed commands.

---

```
Ctrl + R
```

Reverse search command history.

---

# **Quick Revision**

```
Need to find a file?
        │
      find
        │
Need to search text?
        │
      grep
        │
Need first lines?
        │
      head
        │
Need last lines?
        │
      tail
        │
Need counts?
        │
      wc
        │
Need previous commands?
        │
    history
```

---

# **Common Beginner Mistakes (From Our Practice Sessions)**

### Mistake 1

Confusing:

```
find
```

with

```
grep
```

Remember:

- `find` → Finds files/directories.
- `grep` → Finds text inside files.

---

### Mistake 2

Typing the wrong filename while using `grep`.

We faced this during practice when `grep` returned no output because of a typo in the filename.

---

### Mistake 3

Using

```
wc -1
```

instead of

```
wc -l
```

Remember:

- Lowercase **l** = **lines**
- Number **1** is incorrect.

---

### Mistake 4

Forgetting to use `.` in `find`.

Correct:

```
find . -name "*.txt"
```

Without `.` the command is incomplete.

---

### Mistake 5

Thinking `history` only displays commands.

It can also be combined with:

```
history | grep chmod
```

to quickly find previous commands.

---

# **Interview Questions**

1. What is the difference between `find` and `grep`?
2. What is a wildcard?
3. Explain the purpose of `*`.
4. What is the difference between `grep`, `grep -i`, `grep -n`, and `grep -c`?
5. What is a pipe (`|`)?
6. Explain `head` and `tail`.
7. What is `tail -f` used for?
8. What does `wc -l` do?
9. What is the purpose of the `history` command?
10. How can you search your command history?

---

# **Key Takeaways**

- `find` locates **files and directories**, while `grep` searches **inside files**.
- Wildcards (`*`) make searches flexible by matching multiple characters.
- Pipes (`|`) allow commands to work together by passing output from one command to another.
- `head` and `tail` are useful for quickly inspecting large files.
- `wc` provides counts for lines, words, and characters.
- `history` and `Ctrl + R` improve productivity by reusing previous commands.
- Combining commands (e.g., `history | grep chmod`) is one of Linux's most powerful features.