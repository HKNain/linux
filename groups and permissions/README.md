# Linux Groups and Permissions

Linux uses users, groups, and permissions to control who can read, write, or execute files and directories.

## 1. `groupadd` — Create a Group

Creates a new group.

### Syntax

```bash
sudo groupadd groupname
```

### Example

```bash
sudo groupadd developers
```

Creates a group named `developers`.

## 2. `useradd -m` — Create a User with a Home Directory

Creates a new user account and its home directory.

### Syntax

```bash
sudo useradd -m username
```

### Example

```bash
sudo useradd -m harry
```

Creates the user `harry` and typically creates `/home/harry`.

Set a password for the new user:

```bash
sudo passwd harry
```

**Note:** `useradd` is a lower-level utility. On Ubuntu, `sudo adduser harry` is an interactive alternative.

## 3. `passwd` — Set or Change a Password

Sets or changes a user's password.

```bash
sudo passwd harry
```

Changes the password for `harry`.

A user can change their own password using:

```bash
passwd
```

## 4. `usermod -aG` — Add a User to a Group

Adds an existing user to a supplementary group.

### Syntax

```bash
sudo usermod -aG groupname username
```

### Example

```bash
sudo usermod -aG developers harry
```

Adds `harry` to the `developers` group.

To grant administrative privileges on Ubuntu:

```bash
sudo usermod -aG sudo harry
```

**Meaning of the options:**

- `-a`: Append the group without removing other supplementary groups.
- `-G`: Specify supplementary groups.
- `sudo`: Run the command with administrative privileges.

Verify group membership:

```bash
groups harry
```

The user may need to log out and log back in for the new group membership to apply to their session.

## 5. `groups` — Display Group Membership

Shows the groups to which a user belongs.

```bash
groups
```

Shows the current user's groups.

```bash
groups harry
```

Shows the groups associated with `harry`.

## 6. Linux File Permissions

Linux permissions define what actions are allowed for three categories:

| Symbol | Category | Meaning |
|---|---|---|
| `u` | User/owner | Owner of the file |
| `g` | Group | Group associated with the file |
| `o` | Others | All other users |
| `a` | All | User, group, and others |

### The three permissions

| Permission | Symbol | Numeric value | Meaning |
|---|---|---:|---|
| Read | `r` | 4 | Read file contents |
| Write | `w` | 2 | Modify file contents |
| Execute | `x` | 1 | Execute a file or access a directory |

**Easy way to remember:** Read = 4, Write = 2, Execute = 1.

For directories, read allows listing names, write allows changing directory entries, and execute allows traversing or accessing entries subject to permissions.

## 7. `ls -l` — View File Permissions

Displays file details, including permissions, owner, group, size, and modification time.

```bash
ls -l
```

Example output:

```text
-rwxr-x--- 1 harry developers 1200 Oct 29 10:00 script.sh
```

The first 10 characters represent the file type and permissions:

```text
- rwx r-x ---
  u   g   o
```

- `-`: Regular file; `d` indicates a directory.
- `rwx`: Owner can read, write, and execute.
- `r-x`: Group can read and execute, but cannot write.
- `---`: Others have no permissions.

The **nine permission characters** are grouped into three sets of three: owner, group, and others.

## 8. `chmod` — Change File Permissions

Changes the permissions of a file or directory.

### A. Symbolic method

**Give the group write permission:**

```bash
chmod g+w file.txt
```

**Give the owner write permission:**

```bash
chmod u+w file.txt
```

**Remove the owner's write permission:**

```bash
chmod u-w file.txt
```

**Give others read permission:**

```bash
chmod o+r file.txt
```

**Give everyone execute permission:**

```bash
chmod a+x script.sh
```

| Symbol | Meaning |
|---|---|
| `u` | Owner |
| `g` | Group |
| `o` | Others |
| `a` | All |
| `+` | Add a permission |
| `-` | Remove a permission |
| `=` | Set permissions exactly |

### B. Numeric method

Permission values are added together:

- `rwx` = 4 + 2 + 1 = **7**
- `rw-` = 4 + 2 = **6**
- `r-x` = 4 + 1 = **5**
- `r--` = **4**
- `-wx` = 2 + 1 = **3**
- `-w-` = **2**
- `--x` = **1**
- `---` = **0**

Each digit represents owner, group, and others, respectively.

**Example:**

```bash
chmod 754 file.txt
```

This sets:

| Category | Digit | Permission |
|---|---:|---|
| Owner | 7 | `rwx` |
| Group | 5 | `r-x` |
| Others | 4 | `r--` |

Result:

```text
-rwxr-xr--
```

## 9. `chmod 777` — Give Everyone All Permissions

```bash
chmod 777 file.txt
```

This gives the owner, group, and others read, write, and execute permissions.

```text
-rwxrwxrwx
```

Calculation:

- Owner: 7 = `rwx`
- Group: 7 = `rwx`
- Others: 7 = `rwx`

**Security warning:** Avoid `chmod 777` unless there is a specific, justified need. It allows every local user to modify the file and potentially execute it. For directories, it also permits users to create, delete, or rename entries subject to other system protections.

## 10. `chown` — Change File Owner

Changes the owner of a file or directory.

### Syntax

```bash
sudo chown username file.txt
```

### Example

```bash
sudo chown harry file.txt
```

Makes `harry` the owner of `file.txt`.

To change both the owner and group:

```bash
sudo chown harry:developers file.txt
```

## 11. `chgrp` — Change File Group

Changes the group associated with a file or directory.

### Syntax

```bash
sudo chgrp groupname file.txt
```

### Example

```bash
sudo chgrp developers file.txt
```

Changes the group ownership of `file.txt` to `developers`.

### Difference between `chown` and `chgrp`

| Command | Purpose |
|---|---|
| `chown` | Change owner, and optionally group |
| `chgrp` | Change group ownership |

## 12. Complete Practice Example

```bash
# Create a group
sudo groupadd developers

# Create a user with a home directory
sudo useradd -m harry

# Set the user's password
sudo passwd harry

# Add the user to the group
sudo usermod -aG developers harry

# Create a test file
touch file.txt

# Change its owner and group
sudo chown harry:developers file.txt

# Give the group write permission
chmod g+w file.txt

# View permissions
ls -l file.txt

# Set permissions numerically
chmod 754 file.txt

# View the updated permissions
ls -l file.txt
```

## Quick Revision Table

| Command | Purpose |
|---|---|
| `sudo groupadd developers` | Create a group |
| `sudo useradd -m harry` | Create a user and home directory |
| `sudo passwd harry` | Set the user's password |
| `sudo usermod -aG developers harry` | Add a user to a group |
| `groups harry` | Show group membership |
| `ls -l` | Display permissions and ownership |
| `chmod g+w file.txt` | Add group write permission |
| `chmod u+w file.txt` | Add owner write permission |
| `chmod u-w file.txt` | Remove owner write permission |
| `chmod 754 file.txt` | Set `rwxr-xr--` |
| `chmod 777 file.txt` | Give everyone all permissions |
| `sudo chown harry file.txt` | Change the owner |
| `sudo chgrp developers file.txt` | Change the group |

**Exam tip:** Remember the permission order as **owner → group → others**, and the numeric values as **read = 4, write = 2, execute = 1**.