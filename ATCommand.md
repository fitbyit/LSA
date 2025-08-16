The **`at` command** in Linux is used to schedule one-time tasks to be executed at a specific time in the future. It’s useful for running commands or scripts once after some delay or at a particular time without needing repeated execution like with `cron`.

***

## Basic Syntax

```
at [option] time
```

- `time` can be specified in many formats such as `now + 5 minutes`, `10:30 PM`, `tomorrow`, `next Monday`, etc.
- After running the command, you enter the commands to be executed when the time comes, then press Ctrl+D to save.

***

## Common Options

| Option   | Description                                                  |
|----------|--------------------------------------------------------------|
| `-l`     | List the user’s pending `at` jobs (same as `atq`)            |
| `-d`     | Delete a scheduled job by job ID (same as `atrm`)            |
| `-f file`| Read the job commands from a file instead of standard input  |
| `-m`     | Send mail to the user when the job is done                    |
| `-q queue` | Specify a queue to put the job in                           |
| `-c job` | Display the commands of a specified job                       |
| `-V`     | Show version information                                      |

***

## Examples

### 1. Schedule a command interactively at 5 PM
```bash
at 5 PM
# at> echo "Backup started" >> /home/user/backup.log
# at> 
```
The command will run at 5 PM once.

### 2. Schedule a command at a relative time (1 minute from now) from shell
```bash
echo "date >> /tmp/timestamp.log" | at now + 1 minute
```

### 3. List scheduled jobs
```bash
at -l
# or
atq
```

### 4. Remove a scheduled job by job number (e.g., job 2)
```bash
at -d 2
# or
atrm 2
```

### 5. Schedule a script to run tomorrow at 10 AM
```bash
at 10 AM tomorrow -f /path/to/myscript.sh
```

### 6. Schedule a batch job (runs when system load is low)
```bash
echo "/path/to/backup.sh" | batch
```

***

The `at` command is a simple yet powerful tool for one-time scheduled tasks, providing flexibility beyond typical cron usage.
