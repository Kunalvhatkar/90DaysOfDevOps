# Shell Scripting Project: Log Rotation, Backup & Crontab

## Task 1: Log Rotation Script
   Create log_rotate.sh that:
    
    1.	Takes a log directory as an argument (e.g., /var/log/myapp)
    
    2.	Compresses .log files older than 7 days using gzip
    
    3.	Deletes .gz files older than 30 days
    
    4.	Prints how many files were compressed and deleted
    
    5.	Exits with an error if the directory doesn't exist
    
   <img width="1090" height="618" alt="image" src="https://github.com/user-attachments/assets/dcbc8630-3e70-4770-b2c0-2710c121d569" />
   
   <img width="1090" height="97" alt="image" src="https://github.com/user-attachments/assets/80a6991e-31ef-4d3a-bcfb-bf5288c4a855" />

## Task 2: Server Backup Script
   Create backup.sh that:
   
   1.	Takes a source directory and backup destination as arguments
   
   2.	Creates a timestamped .tar.gz archive (e.g., backup-2026-02-08.tar.gz)
   
   3.	Verifies the archive was created successfully
   
   4.	Prints archive name and size
   
   5.	Deletes backups older than 14 days from the destination
   
   6.	Handles errors — exit if source doesn't exist

  <img width="1090" height="997" alt="image" src="https://github.com/user-attachments/assets/2af1ed0e-da3e-4b30-9c4d-6d5bb84d225c" />

  <img width="1090" height="346" alt="image" src="https://github.com/user-attachments/assets/542795c4-84b1-44d8-ad30-399fb2010986" />

## Task 3: Crontab
   1.	Read: crontab -l — what's currently scheduled?
   2.	Understand cron syntax:
      
      
	* * * * *  command
	│ │ │ │ │
	│ │ │ │ └── Day of week (0-6)
	│ │ │ └──── Month (1-12)
	│ │ └────── Day of month (1-31)
	│ └──────── Hour (0-23)
	└────────── Minute (0-59)
   
     
 4. Write cron entries (in your markdown, don't apply if unsure) for:

    o	Run log_rotate.sh every day at 2 AM

    o	Run backup.sh every Sunday at 3 AM

    o	Run a health check script every 5 minutes

   ### Key Crontab Commands
       crontab -e: Edit or create your crontab file.
       crontab -l: List all current cron jobs.
       crontab -r: Remove all cron jobs for the user.
       crontab -u user -e: Edit another user's crontab (requires sudo).

   <img width="1090" height="203" alt="image" src="https://github.com/user-attachments/assets/a79ce0fe-23e0-4665-b7ee-08692903c805" />

## Task 4: Combine — Scheduled Maintenance Script
    Create maintenance.sh that:
      1.	Calls your log rotation function
      2.	Calls your backup function
      3.	Logs all output to /var/log/maintenance.log with timestamps
      4.	Write the cron entry to run it daily at 1 AM
      
   <img width="1091" height="664" alt="image" src="https://github.com/user-attachments/assets/45409b41-27fb-4a34-95d6-a6b295de5a03" />

   <img width="964" height="108" alt="image" src="https://github.com/user-attachments/assets/2d7f3ce1-51b2-4fd0-bf10-6fcee7b71b99" />


  # Learning Point: 
   1. creating backup of files
   2. Compress file and deleted old files
   3. Create a cron job.

