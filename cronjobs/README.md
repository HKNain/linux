# Cron Jobs in Linux

## 1. What is a Cron Job?

A **cron job** is a scheduled task in Linux that runs automatically at a specified time or interval using the cron service.

## 2. Cron Commands

| Command | Description |
|---|---|
| `crontab -l` | Lists the current user's scheduled cron jobs. |
| `crontab -e` | Opens the current user's cron table for editing. |
| `crontab -r` | Removes all cron jobs for the current user. |

## 3. Cron Job Format

A cron expression contains five time fields followed by the command to execute.

```text
* * * * * command
| | | | |
| | | | └── Day of the week (0–7, Sunday)
| | | └──── Month (1–12)
| | └────── Day of the month (1–31)
| └──────── Hour (0–23)
└────────── Minute (0–59)
```

### Special Symbols

| Symbol | Meaning |
|---|---|
| `*` | Every possible value. |
| `,` | Specifies multiple values. |
| `-` | Specifies a range. |
| `/` | Specifies intervals. |

## 4. Examples

Edit the cron table:

```bash
crontab -e
```

List scheduled jobs:

```bash
crontab -l
```

Add these example entries inside the editor:

```cron
* * * * * echo "Hello" >> ~/cron.log
0 * * * * echo "Hourly task" >> ~/cron.log
0 9 * * * /home/user/backup.sh
*/5 * * * * echo "Every 5 minutes" >> ~/cron.log
0 0 * * 0 echo "Weekly task" >> ~/cron.log
```

## 5. Understanding the Examples

| Expression | Execution time |
|---|---|
| `* * * * *` | Every minute. |
| `0 * * * *` | At minute 0 of every hour. |
| `0 9 * * *` | Every day at 9:00 AM. |
| `*/5 * * * *` | Every 5 minutes. |
| `0 0 * * 0` | Every Sunday at midnight. |

**Note:** Replace `/home/user/backup.sh` with the actual script path. Ensure the script has the necessary permissions and use absolute paths where possible.

## Quick Revision

- `crontab -l` — list cron jobs.
- `crontab -e` — edit cron jobs.
- `crontab -r` — remove all cron jobs for the current user.
- `* * * * *` — five time fields representing minute, hour, day of month, month, and day of week.

**Remember:** Cron uses the system's configured time zone, and scheduled jobs run under the permissions of the user whose crontab contains them.