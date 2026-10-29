# Environment Variables, PATH, and .bashrc in Linux

## 1. Environment Variables

Environment variables are named values used by the operating system and programs to store configuration information.

### Commands

| Command | Description |
|---|---|
| `printenv` | Displays environment variables. |
| `env` | Displays environment variables and can run commands with modified environments. |
| `echo $PATH` | Displays the value of the PATH variable. |
| `echo $HOME` | Displays the current user's home directory. |
| `VAR="value"` | Creates or assigns a shell variable. |
| `export VAR="value"` | Creates an environment variable or exports a shell variable. |
| `unset VAR` | Removes a variable from the current shell environment. |

### Examples

```bash
printenv
env
echo $PATH
echo $HOME

NAME="Hitesh"
echo $NAME

export CITY="Rohtak"
echo $CITY

unset CITY
```

**Note:** A shell variable created with `VAR="value"` is not automatically available to child processes. Use `export` to make it an environment variable.

## 2. PATH Variable

`PATH` is an environment variable containing directories where Linux searches for executable commands.

### Examples

```bash
echo $PATH
which ls
```

### Temporarily Add a Directory to PATH

```bash
export PATH="$PATH:$HOME/scripts"
```

This change applies to the current shell and its child processes.

## 3. .bashrc File

`.bashrc` is a configuration file in the user's home directory. It runs when an interactive Bash shell starts and is commonly used to define aliases, environment variables, and shell settings.

### Commands

```bash
cd ~
ls -a
nano ~/.bashrc
```

Add the following lines to `.bashrc`:

```bash
export MY_VAR="Hello"
export PATH="$PATH:$HOME/scripts"
```

Apply the changes without opening a new terminal:

```bash
source ~/.bashrc
```

Verify the variables:

```bash
echo $MY_VAR
echo $PATH
```

**Note:** Changes made directly in a terminal are usually temporary. Add them to `~/.bashrc` to apply them to future interactive Bash sessions.

## 4. Shell Scripts and chmod +x

A shell script is a file containing commands executed by a shell.

### Create a Script

```bash
nano file.sh
```

Write:

```bash
#!/bin/bash
echo "Hello Linux"
echo "$MY_VAR"
```

Save the file, then make it executable:

```bash
chmod +x file.sh
```

Run the script:

```bash
./file.sh
```

Alternatively, run it using Bash:

```bash
bash file.sh
```

**Note:** `chmod +x` adds execute permission; it does not change environment variables.

## 5. Changing Environment Variables

### Temporary Change

```bash
export EDITOR="nano"
echo $EDITOR
```

The change normally lasts only for the current shell session.

### Permanent Change for Interactive Bash

Add the variable to `~/.bashrc`:

```bash
echo 'export EDITOR="nano"' >> ~/.bashrc
source ~/.bashrc
```

### Remove an Environment Variable

```bash
unset EDITOR
```

This removes the variable from the current shell, but a later `.bashrc` reload may define it again.

## Quick Revision

- `printenv` — displays environment variables.
- `env` — displays the environment or runs a command with environment changes.
- `echo $PATH` — displays executable search directories.
- `export VAR="value"` — exports a variable to child processes.
- `~/.bashrc` — stores Bash configuration for interactive shells.
- `source ~/.bashrc` — applies `.bashrc` changes to the current shell.
- `chmod +x file.sh` — gives execute permission to a script.
- `unset VAR` — removes a variable from the current shell.