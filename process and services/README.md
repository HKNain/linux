# Processes and Services in Linux

## 1. Processes

A **process** is a program that is currently running in the operating system. Every process has a unique Process ID (PID).

### Commands

| Command | Description |
|---|---|
| `ps` | Displays processes running in the current terminal. |
| `ps aux` | Displays all running processes with detailed information. |
| `top` | Shows running processes and real-time CPU and memory usage. |
| `htop` | An interactive, user-friendly process monitoring tool. |
| `kill PID` | Sends the default termination signal (SIGTERM) to a process. |
| `kill -9 PID` | Forcefully terminates a process using SIGKILL. |
| `pkill name` | Terminates processes matching a process name or pattern. |

### Examples

```bash
ps
ps aux
top
htop

kill 1234
kill -9 1234
pkill firefox
```

Replace `1234` with the actual PID of the process.

**Note:** Install `htop` if it is unavailable:

```bash
sudo apt install htop
```

## 2. Services

A **service** is a background program that performs tasks such as managing networking, logging, or web servers. On most modern Linux distributions, services are managed by `systemd`.

### `systemctl` Commands

| Command | Description |
|---|---|
| `systemctl status service` | Displays the service's status. |
| `sudo systemctl start service` | Starts a service. |
| `sudo systemctl stop service` | Stops a service. |
| `sudo systemctl restart service` | Stops and starts a service. |
| `sudo systemctl reload service` | Reloads configuration without a full restart, if supported. |
| `sudo systemctl enable service` | Enables a service to start automatically at boot. |
| `sudo systemctl disable service` | Disables automatic startup at boot. |

### Examples

```bash
systemctl status ssh
sudo systemctl start ssh
sudo systemctl stop ssh
sudo systemctl restart ssh
sudo systemctl reload ssh
```

Replace `ssh` with the name of the service you want to manage.

## 3. Difference Between Processes and Services

| Process | Service |
|---|---|
| A running instance of a program. | A program designed to provide a background system function. |
| Identified by a PID. | Commonly managed by `systemctl`. |
| Managed using commands such as `kill` and `pkill`. | Managed using commands such as `systemctl start` and `stop`. |

**Remember:** `kill` manages processes, while `systemctl` manages systemd services.