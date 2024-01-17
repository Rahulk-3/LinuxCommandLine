# Backup Script

## Description

This script is designed to create a compressed archive of specified user directories and save it in the Backups directory. Additionally, it logs the execution time in the backups.log file and any errors in the error.log file.

## Usage

1. Navigate to the home directory:

    ```bash
    pwd /home/rootuser/
    ```

2. Create a Backups directory:

    ```bash
    mkdir ~/Backups/
    ```

3. Create and edit the backup script:

    ```bash
    nano backupscript.sh
    ```

4. Add the following content:

    ```bash
    #! /bin/bash

    tar -czf ~/Backups/ourarchive.tar.gz /{Documents,Pictures,Music,Pictures,Videos} 2>/Backups/error.log
    date >> ~/Backups/backups.log
    mv ~/backup.txt ~/backup_$(date +"%d-%m-%Y")
    ```

5. Make the script executable:

    ```bash
    chmod +x backupscript.sh
    ```

6. Schedule the script to run every 2 minutes:

    ```bash
    crontab -e
    ```

7. Add the following line:

    ```bash
    */2 * * * * bash ~/Backups/backupscript
    ```

8. Save and exit the editor.

9. Save the crontab changes.

10. Run the script manually or wait for the cron job to execute.

## Notes

- The script creates a compressed archive (ourarchive.tar.gz) of specified user directories: Documents, Pictures, Music, Pictures, and Videos.
- Execution logs are stored in the Backups directory (backups.log and error.log).
- The script is scheduled to run every 2 minutes using cron.
