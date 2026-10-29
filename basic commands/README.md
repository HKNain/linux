# Basic Linux Commands

A beginner-friendly guide to essential Linux terminal commands.

## 1. `pwd` — Print Working Directory

Displays the full path of the current directory.

```bash
pwd
```

Example output:

```text
/home/user
```

## 2. `cd` — Change Directory

Used to move from one directory to another.

```bash
cd Documents
```

Moves into the `Documents` directory.

```bash
cd ~
```

Moves to the current user's home directory.

```bash
cd ..
```

Moves one directory level up (to the parent directory).

```bash
cd ../..
```

Moves two directory levels up.

```bash
cd -
```

Returns to the previous working directory.

## 3. `ls` — List Directory Contents

Displays files and directories in the current directory.

```bash
ls
```

Useful options:

```bash
ls -l       # Detailed listing
ls -a       # Show hidden files
ls -lh      # Detailed listing with human-readable file sizes
ls -la      # Show all files with details
```

## 4. `mkdir` — Make Directory

Creates a new directory.

```bash
mkdir projects
```

Creates a directory named `projects`.

### `mkdir -p` — Create Nested Directories

Creates parent directories when they do not exist.

```bash
mkdir -p projects/linux/basics
```

Creates the entire directory structure, including missing parent directories.

**Difference:**
- `mkdir dir` creates a directory if its parent already exists.
- `mkdir -p dir1/dir2` creates missing parent directories as needed.

## 5. `touch` — Create an Empty File

Creates a new empty file if it does not exist.

```bash
touch notes.txt
```

If the file already exists, `touch` updates its access and modification timestamps without changing its contents.

## 6. `vim` — Text Editor

Opens a file in the Vim text editor.

```bash
vim notes.txt
```

If the file does not exist, Vim can create it when you save.

### Basic Vim Commands

| Key/Command | Meaning |
|---|---|
| `i` | Enter Insert mode to type text |
| `Esc` | Return to Normal mode |
| `:w` | Save the file |
| `:q` | Quit Vim |
| `:wq` | Save and quit |
| `:q!` | Quit without saving changes |

**Example workflow:**

1. Run `vim notes.txt`.
2. Press `i` to start typing.
3. Type your text.
4. Press `Esc`.
5. Type `:wq` and press `Enter` to save and exit.

## 7. `cp` — Copy Files and Directories

Copies a file from one location to another.

```bash
cp notes.txt backup.txt
```

Copies `notes.txt` to a new file named `backup.txt`.

```bash
cp notes.txt Documents/
```

Copies the file into the `Documents` directory.

```bash
cp -r projects projects_backup
```

Copies a directory and its contents recursively.

**Note:** Be careful when copying over an existing file, because its contents may be overwritten.

## 8. `cat` — Display File Contents

Displays the contents of a file in the terminal.

```bash
cat notes.txt
```

You can also combine multiple files:

```bash
cat file1.txt file2.txt
```

This displays the contents of both files consecutively.

## 9. `cat -n` — Display Contents with Line Numbers

Displays a file with line numbers.

```bash
cat -n notes.txt
```

Example output:

```text
     1  Hello Linux
     2  Learning commands
     3  Practice every day
```

Unlike plain `cat`, this option numbers the displayed lines, including blank lines.

## 10. `less` — View a File Page by Page

Used to read large files one screen at a time.

```bash
less notes.txt
```

### Useful Keys in `less`

| Key | Meaning |
|---|---|
| `Space` | Next page |
| `b` | Previous page |
| `Enter` | Move down one line |
| `/word` | Search for a word |
| `n` | Next search result |
| `q` | Quit |

**Difference between `cat` and `less`:**
- `cat` displays the contents directly.
- `less` lets you navigate through the file without displaying everything at once.

## 11. `history` — View Previous Commands

Displays commands previously entered in the terminal.

```bash
history
```

Display the last 10 commands:

```bash
history 10
```

Search command history:

```bash
history | grep mkdir
```

This displays history entries containing `mkdir`.

## 12. `cd ~` — Go to the Home Directory

The tilde (`~`) represents the current user's home directory.

```bash
cd ~
```

Example:

```text
/home/user
```

The exact path depends on the user and system.

## 13. `../` — Parent Directory

The expression `..` refers to the parent directory.

```bash
cd ..
```

Example: If your current directory is:

```text
/home/user/Documents
```

Running `cd ..` moves you to:

```text
/home/user
```

You can also use the parent-directory path when accessing files:

```bash
cat ../notes.txt
```

This attempts to display `notes.txt` from the parent directory.

## 14. `./` — Current Directory

The expression `.` refers to the current directory.

```bash
ls ./
```

Lists the contents of the current directory.

You can use `./` to refer to a file in the current directory:

```bash
cat ./notes.txt
```

You can also execute a script or program in the current directory:

```bash
./script.sh
```

The script must have execute permission and a valid interpreter or executable format.

## Quick Revision Table

| Command | Purpose |
|---|---|
| `pwd` | Show the current directory path |
| `cd dir` | Change directory |
| `cd ~` | Go to the home directory |
| `cd ..` | Go to the parent directory |
| `cd -` | Return to the previous directory |
| `ls` | List files and directories |
| `mkdir dir` | Create a directory |
| `mkdir -p a/b` | Create nested directories |
| `touch file.txt` | Create an empty file |
| `vim file.txt` | Open a file in Vim |
| `cp a.txt b.txt` | Copy a file |
| `cp -r a b` | Copy a directory recursively |
| `cat file.txt` | Display file contents |
| `cat -n file.txt` | Display contents with line numbers |
| `less file.txt` | Read a file page by page |
| `history` | Show previously entered commands |
| `.` or `./` | Refer to the current directory |
| `..` or `../` | Refer to the parent directory |
| `~` | Refer to the home directory |

**Tip:** Linux commands are case-sensitive. For example, `Documents` and `documents` can be different directories.