Backup Script

Description

This script is designed to create a compressed archive of specified user directories and save it in the Backups directory. Additionally, it logs the execution time in the backups.log file and any errors in the error.log file.

Usage
Navigate to the home directory:

bash
Copy code
pwd
/home/rootuser/
Create a Backups directory:

bash
Copy code
mkdir ~/Backups/
Create and edit the backup script:

bash
Copy code
nano backupscript.sh
Add the following content:

bash
Copy code
#! /bin/bash

tar -czf ~/Backups/ourarchive.tar.gz ~/{Documents,Pictures,Music,Pictures,Videos} 2>~/Backups/error.log
date >> ~/Backups/backups.log
mv ~/backup.txt ~/backup_$(date +"%d-%m-%Y")
Make the script executable:

bash
Copy code
chmod +x backupscript.sh
Schedule the script to run every 2 minutes:

bash
Copy code
crontab -e
Add the following line:

bash
Copy code
*/2 * * * * bash ~/Backups/backupscript
Save and exit the editor.

Save the crontab changes.

Run the script manually or wait for the cron job to execute.

Notes
The script creates a compressed archive (ourarchive.tar.gz) of specified user directories: Documents, Pictures, Music, Pictures, and Videos.
Execution logs are stored in the Backups directory (backups.log and error.log).
The script is scheduled to run every 2 minutes using cron.
