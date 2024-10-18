# Linux_notes

To remove old log files while keeping recent ones, you can use find and rm commands in Linux. If you want to delete log files based on their age or keep a certain number of recent files, here are a few options:

1. Remove Log Files Older Than X Days

If you want to delete log files older than, for example, 30 days, you can run:

find /path/to/logs/ -type f -name "*.log" -mtime +30 -exec rm {} \;

/path/to/logs/: Replace with the actual directory where your logs are stored.

-mtime +30: Finds files older than 30 days.

-name "*.log": Ensures only log files (with .log extension) are selected.

-exec rm {}: Deletes the files found.


2. Keep Only the Latest X Files (Based on Time)

To remove older files while keeping only the latest 100 files (based on modification time), you can use this combination of ls and rm:

ls -t /path/to/logs/*.log | tail -n +101 | xargs rm

ls -t: Lists files sorted by modification time (newest first).

tail -n +101: Skips the first 100 files and lists the rest.

xargs rm: Deletes the files listed.


3. Remove Files Larger Than a Certain Size

If you want to remove log files that exceed a certain size (e.g., 500 MB), use:

find /path/to/logs/ -type f -name "*.log" -size +500M -exec rm {} \;

This way, you can target specific criteria for removing the log files efficiently.
