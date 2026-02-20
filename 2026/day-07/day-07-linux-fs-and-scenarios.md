  # Day 07 – Linux File System Hierarchy & Scenario-Based Practice

## Part 1: File System Hierarchy:
1.	In Linux Everything is a file and directory including a hardware program. Files are stored in directory.
2.	Directory contains a file with tree structure. That’s called File System Hierarchy.
<img width="1016" height="469" alt="image" src="https://github.com/user-attachments/assets/526a9ee4-e314-4b30-9493-0f1bc5eac004" />

## Core Directories in Linux FileSystem:
a.	root directory / : 
  •	All Linux systems have a directory structure that starts at the root directory.
  •	Everything that exists on your Linux system can be found below this root directory. All files and directories come under this root directory.
  •	It is like the top-level parent folder of the entire system. 
  
  <img width="981" height="115" alt="image" src="https://github.com/user-attachments/assets/64f008f4-a86f-49d7-9ebd-349e8bf2e6b3" />

b.	/home :   
    •	This directory contains home folders of normal users.
    •	Each user gets their own folder here to store personal files, documents, scripts, etc.
    
    <img width="734" height="109" alt="image" src="https://github.com/user-attachments/assets/39314c3a-f76a-4560-accc-893c5b9ae7ec" />

c.	/root : 
    •	It is the home directory for the root user (superuser). 
    •	It is different from /home and only accessible by the root user. Root user stores admin-related files here.

d.	/etc : 
    •	This directory contains system configuration files. 
    •	Important configurations like network settings, user accounts, services, and software configurations are stored here.
    
  <img width="1023" height="524" alt="image" src="https://github.com/user-attachments/assets/1923e6a0-0a37-435a-ba65-01444390d9c6" />

e.	/var/log :
    •	This directory stores system and service log files.
    •	Logs help in troubleshooting errors and monitoring services like nginx, ssh, etc.  
    
  <img width="1051" height="149" alt="image" src="https://github.com/user-attachments/assets/9abd1840-5046-44b9-8bb4-b8fc44a09afc" />

f.	/tmp  : 
    •	This directory stores temporary files created by the system and applications. It is used for temporary data storage.
    •	Files here are usually deleted automatically after reboot. 
      
  <img width="1059" height="256" alt="image" src="https://github.com/user-attachments/assets/bf7af2e3-bdaa-480a-a3e7-903a1ba9890d" />

## Additional Directories:  
a.	/bin :
      •	This directory contains essential system commands required for basic operation. Commands like ls, cp, mv, cat, and rm are stored here.
      •	 These commands are needed even when no other filesystem is mounted.
      
  <img width="981" height="681" alt="image" src="https://github.com/user-attachments/assets/77627cb8-e292-427f-b6a3-8df12465b9ef" />

b.	/usr/bin : 
      •	This directory contains most of the user-level commands and software binaries. It includes programs like nano, vim, git, python, etc. These are used by normal users for daily tasks. 
      
  <img width="978" height="638" alt="image" src="https://github.com/user-attachments/assets/d0bc9e28-c32f-422f-ba04-6cc90318ac83" />

c.	/opt :
      •	This directory is used to install optional and third-party applications. Software like Docker, custom applications, or vendor tools are often installed here. 
      •	It helps keep third-party software separate from system files. 
      
  <img width="671" height="56" alt="image" src="https://github.com/user-attachments/assets/5a9de302-9e66-4fbd-95ab-267ce5f4c50c" />

## Hands on Task : 
1.	du -sh /var/log/* 2>/dev/null | sort -h | tail -5 :  
    •	This command checks the size of all log files in /var/log directory. 
    •	It then sorts them and shows the 5 largest log files. This helps to find which logs are using more disk space for troubleshooting and cleanup.
    •	2>/dev/null: its throw error in null space this space doesn’t exist in system. (Throw in trash or black hole)

     <img width="1090" height="202" alt="image" src="https://github.com/user-attachments/assets/7adfa133-4804-45fb-b746-d39aeb7ca55f" />
 
3.	cat /etc/hostname :  
    •	This command is used to display hostname of the system.
    •	The hostname is the name given to the server or computer on a network.

  	<img width="678" height="103" alt="image" src="https://github.com/user-attachments/assets/e8d92d4a-1bbd-4f0c-b58c-3e47b5b48a7a" />

5.	ls -la ~ : 
    •	list all files and directories in the current user’s home directory with detailed information.
    •	It shows hidden files, permissions, owner, size, and modification date.

  	<img width="1045" height="443" alt="image" src="https://github.com/user-attachments/assets/ea8ad617-05f6-4462-8885-5c05c97ca8ab" />

## Part 2: Scenario-Based Practice 
### Scenario 1: Service Not Starting 
    Step 1 : Check status of “myapp” service using command “sudo systemctl status myapp”.
    Reason: This command checks whether the myapp service is running, stopped or failed, and shows basic error information.
    Step 2: Check log of myapp service using command “sudo journalctl -u myapp -n 50”.
    Reason: This command shows the last 50 log entries of my app service that helps to find exact error causing the failure.
    Step 3: Check service is enabled or not using command “systemctl is-enabled myapp”
    Reason: This command checks whether the service is enabled to start automatically after system reboot.
    Step 4: check myapp service exists in the system using command 
            “systemctl list-units –type=service | grep myapp”.
    Reason: This command verifies whether the myapp service exists in the system.
    Outcome: First check the service status, then check the logs for errors, and service is enabled and properly configured.

### Scenario 2: High CPU Usage 
    Step1: Check CPU usage and running process using “top” command.
    Reason: shows CPU usage.
    Step 2: sort processes by highest CPU usage. Ps aux –sort=-%cpu | head -19
    Reason: list the top 10 processes that use highest CPU along with their PID.
    Step 3: use “htop” command it makes easier to identify high CPU consuming processes.
    Reason 4: user-friendly and colourful view of CPU usage, making it easier to identify high CPU consuming processes.
    Outcome: First monitor live CPU usage, then identify the top CPU consuming process and its ID. 

### Scenario 3: Finding Service Logs (docker)
    Step 1: Check Docker service status. “sudo systemctl status docker”
    Reason: Checks docker service is running and shows basic log and errors.
    Step 2: check last 50 lines of docker service logs. “journalctl -u docker -n 50”
    Reason: Check recent activity and error.
    Step 3: check real time docker log. “journalctl -u docker -f”
    Reason: helping to monitor live service activity. 

### Scenario 4: File Permissions Issue
    Step 1: Check current permission of backup.sh “ls -l /backup.sh”  
    
  <img width="809" height="91" alt="image" src="https://github.com/user-attachments/assets/876be478-3615-44e4-9b29-5eb6b26c0cfd" />

    Reason: This command shows the current file permissions and confirms that the file does not have execute (x) permission.
    
    Step 2: Add execute permission. “chmod +x backup.sh”  
    
  <img width="831" height="128" alt="image" src="https://github.com/user-attachments/assets/d10e3b21-dc82-49a2-a5f5-b2ae1ea3cda9" />
 
    Reason: This command adds execute permission so the script can be run.
    
    Step 3: Verify execute permission added  
    
  <img width="804" height="103" alt="image" src="https://github.com/user-attachments/assets/c5ffa4b5-d763-445f-9ba5-0ac27956ae35" />
 
    Reason: confirms that execute (x) permission is successfully added.
    
    Step 4: Run the script 
    
  <img width="763" height="126" alt="image" src="https://github.com/user-attachments/assets/5ed3a629-c290-4658-965d-1ee2df3ccf60" />
   
 

