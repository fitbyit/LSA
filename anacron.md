## What is Anacron

**Anacron** is a scheduling tool like cron, but it's specially designed for systems that are not always running—such as laptops or desktops that might be powered off sometimes.

## Basic Anacron Job Syntax

In the configuration file `/etc/anacrontab` each job is written as:

```
period delay job-identifier command
```
- **period:** How often, in days, the job should run (e.g., 1 for daily, 7 for weekly)
- **delay:** How many minutes after system boot before the job is run
- **job-identifier:** A short label for the job
- **command:** The script or command to execute

### Example of anacrontab entry

To run a backup every day, 15 minutes after the computer starts:

```
1 15 daily-backup /home/user/backup.sh
```
This asks anacron to:
- Run `/home/user/backup.sh`
- Once every day (`1`)
- 15 minutes after the computer has turned on
- Identified as `daily-backup` for logging/tracking.

## How to Use Anacron

1. Edit `/etc/anacrontab` as root.
2. Add your job using the syntax above.
3. Make sure Anacron service is enabled (usually it runs automatically on most distributions, including RHEL).

## How it Differs from Cron

| Feature                 | Cron                                      | Anacron                                     |
|-------------------------|-------------------------------------------|---------------------------------------------|
| **Precision**           | Minute-level                              | Day-level                                   |
| **Type of system**      | Always-on (servers)                       | Non-continuous/desktops/laptops             |
| **Missed jobs**         | Are skipped                               | Run at next startup                         |
| **Configuration**       | Per-user (`crontab -e`) and system-wide   | System-wide (`/etc/anacrontab`)             |
