# AutoBk Docs
## What is it?
AutoBk is a set of custom Python scripts built to provide automated and centralized backup to devices and equipment that doesn't ordinarily have this functionality, or only provides properietary solutions.

Any protocol or method that Python can do can be used, from SSH and SCPing pre-built files, to web scraping a form, to clicking a "Backup Now" button in a web interface. 

## How does it work?
It works based on a constantly running process on the backup server itself (`srvc_autobk.py`), ordinarily run as a systemd service to allow cleaner stop/start/restart.

This service runs in a cycle, with a default sleep duration of 60 seconds. There are three tasks that are completed during each cycle:
- **Maintenance:** Deletes expired backups (`op_autobk_maintenance.py`)
- **Scheduling:** Schedules backup times based on device settings (`op_autobk_scheduling.py`)
- **Backup:** The actual functional process that calls a specific set of scripts to backup devices. (`op_autobk_backups.py`)



