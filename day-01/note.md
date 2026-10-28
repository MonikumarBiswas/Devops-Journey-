# Day 01: Basic Linux File and Text Commands

**Learning goal:** Create, view, copy, move, and delete files and directories using the Linux terminal. Learn how to read text files and inspect logs.

## 1. Commands Covered

| No. | Command | Purpose |
|---:|---|---|
| 1 | `mkdir` | Create directories |
| 2 | `touch` | Create empty files |
| 3 | `nano` | Edit text files |
| 4 | `cat` | Display file contents |
| 5 | `cp` | Copy files and directories |
| 6 | `mv` | Move or rename files |
| 7 | `rm -r` | Remove directories and their contents |
| 8 | `head` | Display the beginning of a file |
| 9 | `tail` | Display the end of a file |
| 10 | `tail -f` | Follow a growing log file |
| 11 | `less` | Read long files page by page |
| 12 | `ls` | List files and directories |

---

## 2. Creating Files and Directories

### `mkdir` — Make a directory

Create a directory:

```bash
mkdir projects
```

Create nested directories, including missing parent directories:

```bash
mkdir -p projects/devops/notes
```

**Key point:** The `-p` option creates parent directories when necessary.

### `touch` — Create files

Create an empty file:

```bash
touch notes.txt
```

Create multiple files at once:

```bash
touch a.txt b.txt c.txt
```

**Note:** If a file already exists, `touch` updates its modification timestamp without replacing its contents.

### `nano` — Edit a text file

```bash
nano notes.txt
```

Useful keyboard shortcuts:

| Shortcut | Action |
|---|---|
| `Ctrl + O` | Save the file |
| `Enter` | Confirm the filename |
| `Ctrl + X` | Exit Nano |

---

## 3. Viewing File Contents

### `cat` — Display the entire file

```bash
cat notes.txt
```

Best for short files. For large files, use `less`.

### `head` — View the beginning

```bash
head notes.txt
head -n 5 notes.txt
```

- `head notes.txt` displays the first 10 lines by default.
- `head -n 5 notes.txt` displays the first 5 lines.

### `tail` — View the end

```bash
tail notes.txt
tail -n 20 notes.txt
```

- `tail notes.txt` displays the last 10 lines by default.
- `tail -n 20 notes.txt` displays the last 20 lines.

### `tail -f` — Monitor a growing log

```bash
tail -f /var/log/syslog
```

This displays new lines as they are added to the log file. It is useful for monitoring application and system activity.

Press `Ctrl + C` to stop following the file.

**Important:** The log path depends on your Linux distribution. Some systems use `/var/log/messages` or the system journal. You may need elevated permissions to read system logs.

### `less` — Read long files page by page

```bash
less /var/log/syslog
```

Useful keyboard shortcuts:

| Key | Action |
|---|---|
| `Space` or `f` | Next page |
| `b` | Previous page |
| `/word` | Search for a word |
| `n` | Find the next match |
| `q` | Quit |

---

## 4. Copying, Moving, and Deleting

### `cp` — Copy files

```bash
cp notes.txt notes_backup.txt
```

Copy a directory and its contents:

```bash
cp -r projects projects_backup
```

**Key point:** Use `-r` to copy directories recursively.

### `mv` — Move or rename files

Move a file into a directory:

```bash
mv notes.txt projects/
```

Rename a file:

```bash
mv old_name.txt new_name.txt
```

**Key point:** `mv` can move files between locations or rename them.

### `rm` — Remove files and directories

Delete a file:

```bash
rm notes_backup.txt
```

Delete a directory and everything inside it:

```bash
rm -r projects_backup
```

> **⚠️ Safety warning:** Terminal deletion usually bypasses the desktop Trash. Check the target path before running `rm -r`. Be especially careful with `rm -rf`, which can delete files recursively without prompting.

---

## 5. Listing Files with `ls`

| Command | Purpose |
|---|---|
| `ls` | List files and directories |
| `ls -a` | Include hidden files |
| `ls -l` | Show permissions, owner, size, and modification time |
| `ls -lh` | Show file sizes in human-readable units |
| `ls -la` | Show detailed information, including hidden files |
| `ls -R` | List subdirectories recursively |

### Examples

```bash
ls
ls -a
ls -lh
ls -la
ls -R
```

**Remember:**
- Hidden files usually start with a dot (`.`), such as `.gitignore`.
- `-l` means long listing format.
- `-h` makes sizes easier to read.
- `-R` means recursive listing.

---

## 6. Hands-on Practice

### Objective

Create a directory, create files, write content, copy a file, rename another file, inspect the results, and clean up.

### Commands I ran

```bash
mkdir -p practice/day1
cd practice/day1

touch a.txt b.txt
echo "hello linux" > a.txt

cp a.txt c.txt
mv b.txt notes.txt

ls -la
cat a.txt

cd ..
rm -r day1
```

### Expected results

| Command | What happens |
|---|---|
| `mkdir -p practice/day1` | Creates the nested directories |
| `touch a.txt b.txt` | Creates two empty files |
| `echo "hello linux" > a.txt` | Writes text into `a.txt` |
| `cp a.txt c.txt` | Creates a copy named `c.txt` |
| `mv b.txt notes.txt` | Renames `b.txt` |
| `ls -la` | Lists files, including hidden entries |
| `cat a.txt` | Displays `hello linux` |
| `cd ..` | Moves to the parent directory |
| `rm -r day1` | Deletes the `day1` directory and its contents |

**Observation:** The `>` operator writes output to a file and replaces its existing contents. Use `>>` when you want to append instead.

### Verification challenge

Before deleting anything, try:

```bash
pwd
ls -la
ls -la practice/day1
```

Check the current location and directory contents before cleanup.

---

## 7. What I Learned

- How to create files and directories from the terminal.
- How to inspect short and long text files.
- How to monitor log files using `tail -f`.
- How to copy, move, rename, and delete files.
- How to use common `ls` options.
- Why checking paths matters before deleting files.

## 8. Next Steps

- [ ] Practise each command without copying the examples.
- [ ] Learn file permissions: `chmod` and `chown`.
- [ ] Learn input/output redirection: `>`, `>>`, and `2>`.
- [ ] Commit these notes to GitHub.

**Status:** ✅ Day 01 completed
