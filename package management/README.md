# Linux Package Management with APT

APT (Advanced Package Tool) is used to manage software packages on Ubuntu and Debian-based Linux distributions. It allows you to update package information, install software, upgrade packages, and remove applications.

## 1. `sudo apt update` — Update Package Lists

Downloads the latest package information from configured software repositories.

```bash
sudo apt update
```

**Remember:** This updates the package lists, not the installed software itself.

## 2. `sudo apt install` — Install Packages

Installs a package and its required dependencies.

### Syntax

```bash
sudo apt install package_name
```

### Example

```bash
sudo apt install vim
```

Installs the Vim text editor.

Install multiple packages at once:

```bash
sudo apt install vim git curl
```

## 3. `sudo apt upgrade` — Upgrade Installed Packages

Upgrades installed packages to newer available versions based on the updated package lists.

```bash
sudo apt upgrade
```

To proceed without an interactive confirmation prompt:

```bash
sudo apt upgrade -y
```

**Note:** The `-y` option automatically answers yes to confirmation prompts.

## 4. `sudo apt remove` — Remove a Package

Uninstalls a package but generally leaves its system-wide configuration files behind.

### Syntax

```bash
sudo apt remove package_name
```

### Example

```bash
sudo apt remove vim
```

Removes the Vim package.

## 5. `sudo apt purge` — Remove a Package and Its Configuration

Removes a package along with its package-managed system configuration files.

```bash
sudo apt purge vim
```

**Difference:**
- `remove` removes the package but generally retains system configuration.
- `purge` removes the package and its package-managed configuration.

Neither command necessarily removes every file the application created in your home directory.

## 6. `sudo apt show` — Display Package Information

Displays information about a package, such as its version, dependencies, description, and repository details.

### Syntax

```bash
apt show package_name
```

### Example

```bash
apt show vim
```

You generally do not need `sudo` for this command.

## 7. `apt list` — List Packages

Displays information about packages known to APT.

### List installed packages

```bash
apt list --installed
```

Shows packages currently installed on the system.

### List upgradeable packages

```bash
apt list --upgradable
```

Shows installed packages with available upgrades.

### Search package names

```bash
apt list --all-versions vim
```

Lists available versions of Vim known to APT.

## 8. `apt search` — Search for Packages

Searches package names and descriptions for a keyword.

```bash
apt search python
```

Useful when you know what software you need but not its exact package name.

## 9. `sudo apt autoremove` — Remove Unneeded Dependencies

Removes automatically installed packages that are no longer needed.

```bash
sudo apt autoremove
```

Review the packages APT proposes to remove before confirming.

## 10. `--install` vs `--installed`

The common option for listing installed packages is:

```bash
apt list --installed
```

`--installed` is a listing filter. It is not the same as the `install` subcommand.

To install a package, use:

```bash
sudo apt install git
```

## Quick Revision Table

| Command | Purpose |
|---|---|
| `sudo apt update` | Refresh package lists |
| `sudo apt install vim` | Install Vim |
| `sudo apt upgrade` | Upgrade installed packages |
| `sudo apt remove vim` | Remove Vim, generally retaining configuration |
| `sudo apt purge vim` | Remove Vim and package-managed configuration |
| `apt show vim` | Show package details |
| `apt list --installed` | List installed packages |
| `apt list --upgradable` | List packages with available upgrades |
| `apt search git` | Search for packages |
| `sudo apt autoremove` | Remove unneeded dependencies |

## Recommended Workflow

```bash
# Refresh package information
sudo apt update

# Install software
sudo apt install git

# Upgrade installed packages
sudo apt upgrade

# Check installed packages
apt list --installed

# View package information
apt show git

# Remove software when no longer needed
sudo apt remove git
```

**Tip:** Run `sudo apt update` before installing or upgrading software so APT uses current package information. Review removal and upgrade prompts before confirming.