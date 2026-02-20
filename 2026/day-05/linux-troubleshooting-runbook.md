# Day 05 Task: Linux Troubleshooting Drill: CPU, Memory, and Logs.

## 1.	Target service / process : 
  a.	Sudo systemctl status nginx : check ststus of nginx service.   <img width="973" height="459" alt="image" src="https://github.com/user-attachments/assets/283a4424-f838-48ca-922f-92c477d0c915" />


## 2.	Environment Basics : 
a.	Uname -a : shows all information about linux system. <img width="1000" height="120" alt="image" src="https://github.com/user-attachments/assets/4dc55111-ab67-4348-8885-8668785aff84" />
      
b.	Cat /etc/os-release : P{rovides information about Operating System Distribution and version. <img width="965" height="411" alt="image" src="https://github.com/user-attachments/assets/a5639f9b-8c7b-42a2-96c1-b2df17953f55" />

## 3. File System Sanity:
a.	mkdir /tmp/runbook-demo : Creates a new directory named runbook-demo inside the /tmp directory in Linux. /tmp allows users to create temporary folders for scripts or working files. <img width="950" height="278" alt="image" src="https://github.com/user-attachments/assets/d2940ced-7c84-4f0d-a44d-742855395fe1" />
      
b.	cp /etc/hosts /tmp/runbook-demo/hosts-copy :  Copies the system's network hosts file (/etc/hosts) to a new file named hosts-copy inside the /tmp/runbook-demo/ directory. <img width="971" height="159" alt="image" src="https://github.com/user-attachments/assets/243d1661-e501-430a-a0b8-8421a7c80e08" />

## 4.	CPU / Memory health checks: 
a.	free -h : used to display the amount of free and used memory (RAM) and swap space in the system in a human-readable format. <img width="966" height="141" alt="image" src="https://github.com/user-attachments/assets/33baed09-a0ee-40ac-9df1-a2961f9c2994" />
      
b.	ps -ef | grep nginx :  Lists every process running on the system with full details.Filters the list to only show lines containing the word "nginx". <img width="983" height="190" alt="image" src="https://github.com/user-attachments/assets/dee1a6e7-f718-4e7c-a297-bee649c27a19" />

## 5.	Disk / IO: 
a.	df -h : display information about total space and available space on a file system. <img width="955" height="325" alt="image" src="https://github.com/user-attachments/assets/3c4344b1-81f5-4bf6-a94e-18fcf17af6c9" />
      
b.	du -sh /var/log : display the disk usage of all the directories in /var/log. <img width="829" height="109" alt="image" src="https://github.com/user-attachments/assets/1c7dbc15-f915-4859-8f09-ba81aed86ef4" />

## 6. Network: 
a.	sudo ss -tulpn | grep nginx : to identify the network ports and sockets that the Nginx web server is currently using. <img width="960" height="173" alt="image" src="https://github.com/user-attachments/assets/6d131bb9-0b57-44f8-afd2-620a5412846e" />

b.	curl -I http://localhost : a quick way to check if a local web server is responding. <img width="931" height="310" alt="image" src="https://github.com/user-attachments/assets/8bd56a33-39b8-4163-95af-7fff3b5bede6" />

## 7. Log Command: 
a.	sudo journalctl -u nginx -n 50 : It used to troubleshoot Nginx by viewing its most recent system logs. <img width="920" height="351" alt="image" src="https://github.com/user-attachments/assets/37f427ca-16ff-4c35-ace5-40620cc5fd0f" />

b.	tail -n 50 /var/log/nginx/error.log : It used in Linux to view the last 50 lines of the Nginx error log file. <img width="981" height="104" alt="image" src="https://github.com/user-attachments/assets/fbaecd20-8ceb-4657-83e2-55542e4e2c55" />

## 8. Quick findings:
1.	nginx service run normally.
2.	CPU, memory, disk, and network usage are healthy.
3.	No errors found in logs.

## 9 If this worsens:

1. Restart nginx service using "sudo systemctl restart nginx". <img width="721" height="27" alt="image" src="https://github.com/user-attachments/assets/7bb8d2c5-639e-4bdc-8bab-6fef8890099a" />

2. Check detailed real time logs using "journalctl -u nginx -f". <img width="1463" height="442" alt="image" src="https://github.com/user-attachments/assets/597b0cdb-a2d6-4f24-82ad-b630a3d94f87" />

3. Monitor process using "top" command. <img width="1390" height="630" alt="image" src="https://github.com/user-attachments/assets/21131a39-6b0e-46f6-bb74-cdfd311799b6" />

4. Check disk full issue
5. Reinstall nginx if corrupted
