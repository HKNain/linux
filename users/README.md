# Linux User Management Commands

This guide covers basic Linux commands for checking the current user, creating users, switching users, and granting administrative privileges.

## 1. `whoami` — Check the Current User

Displays the username of the user currently logged in.

### Syntax

```bash
whoami
```

Example output:

```text
hitesh
```

## 2. `sudo adduser` — Create a New User

Creates a new user account on the system.

### Syntax

```bash
sudo adduser username
```

### Example

```bash
sudo adduser harry
```

This creates a user named `harry`.

You may be prompted to:
- Enter and confirm a password.
- Enter optional user information.
- Confirm the entered information.

On Ubuntu, `adduser` is an interactive, user-friendly command.

## 3. `su - username` — Switch to Another User

Switches to another user account and starts a login shell with that user's environment.

### Syntax

```bash
su - username
```

### Example

```bash
su - harry
```

You will generally need to enter `harry`'s password.

To verify the switch:

```bash
whoami
```

Expected output:

```text
harry
```

To return to your previous shell, run:

```bash
exit
```

**Note:** The `-` in `su - username` loads the target user's login environment, including their home directory.

## 4. `sudo usermod -aG sudo username` — Give a User Sudo Access

Adds an existing user to the `sudo` group, allowing them to use administrative commands on Ubuntu and other systems configured to grant privileges through that group.

### Syntax

```bash
sudo usermod -aG sudo username
```

### Example

```bash
sudo usermod -aG sudo harry
```

This adds `harry` to the `sudo` group.

**Meaning of the options:**

| Option | Meaning |
|---|---|
| `-u` | Modify a user's account (part of the command `usermod`) |
| `-a` | Append the user to the specified supplementary group(s) |
| `-G` | Specify supplementary groups |
| `sudo` | The group name that grants administrative access on Ubuntu |

**Important:** Always use `-aG` together when adding a supplementary group. Using `-G` without `-a` can remove the user from other supplementary groups.

The user may need to log out and log back in for the new group membership to take effect in their session.

To verify group membership:

```bash
groups harry
```

## 5. `sudo -l` — Check Sudo Permissions

Shows which commands the current user is permitted to run with `sudo`.

```bash
sudo -l
```

Run this command as the user whose permissions you want to inspect.

## 6. Complete Practice Example

The following commands demonstrate the basic workflow on Ubuntu:

```bash
# Check the current user
whoami

# Create a new user
sudo adduser harry

# Switch to the new user
su - harry

# Check the current user again
whoami

# Return to the previous user
exit

# Add harry to the sudo group
sudo usermod -aG sudo harry

# Verify group membership
groups harry
```

The final command should list `sudo` among the user's groups if the operation succeeded.

**Security tip:** Only grant sudo privileges to trusted users. Members of the sudo group can perform powerful administrative operations on the system.