## What is a Cron Job?

- A cron job is a scheduled task that runs automatically at specified times or intervals.
- Cron jobs are managed using the `crontab` command.

***

## Cron Syntax

Each cron job line in `crontab` follows this pattern:

```
* * * * * command_to_run
- - - - -
| | | | |
| | | | +---- Day of week (0-7, Sunday is 0 or 7)
| | | +------ Month (1-12)
| | +-------- Day of month (1-31)
| +---------- Hour (0-23)
+------------ Minute (0-59)
```

***

## Basic Commands

- Edit your cron jobs: `crontab -e`
- View your cron jobs: `crontab -l`

***

## Simple Examples

| Task                                      | Cron Expression               | What it Does                                |
|--------------------------------------------|-------------------------------|---------------------------------------------|
| Run every minute                          | `* * * * * /path/to/script`   | Runs every minute                           |
| Run every 15 minutes                      | `*/15 * * * * /path/to/script`| Runs at 15 minutes                          |
| Run at 3:00 PM daily                      | `0 15 * * * /path/to/script`  | Runs every day at 3:00PM                    |
| Run at 9:00 AM on weekdays (Mon-Fri)      | `0 9 * * 1-5 /path/to/script` | Runs at 9:00AM, Monday through Friday       |
| Run at midnight every day                 | `0 0 * * * /path/to/script`   | Runs daily at midnight                      |
| Run at 8:30 AM, 10th of June              | `30 8 10 6 * /path/to/script` | Every year, June 10 at 8:30AM               |

Replace `/path/to/script` with the script or command you want to run.

***

## How to Set a Cron Job

1. Run: `crontab -e`
2. Add the desired line (as per the examples above).
3. Save and exit. Your scheduled job is now set!

***

## Example: Running a Script Every Hour

Create a script : `gedit every_minute_log.sh` and add below code

```
#!/bin/bash

# Output file
OUTPUT_FILE="/home/admin/every_minute_log.txt"

# Write the current date and time to the file
echo "Script ran at $(date)" >> "$OUTPUT_FILE"
```

Open your crontab editor:
```
crontab -e
```
Add:
```
*/2 * * * * /home/admin/every_minute_log.sh
```
This runs `every_minute_log.sh` every minute.

To check cron jobs :
```
crontab -l
```

***
