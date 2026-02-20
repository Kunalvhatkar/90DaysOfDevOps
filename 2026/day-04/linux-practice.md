# Process Checks : 
1. ps : Process status , list all currently running process on the system.It is fundamental tool for system monitoring and toubleshooting.


   <img width="746" height="190" alt="image" src="https://github.com/user-attachments/assets/7a9dc5ad-1cf1-4d04-b517-0d15d9a94fa4" />
        
2. top : provides a dynamic realtime view of running system.acts like "Task Manager" , display system information.


   <img width="1090" height="370" alt="image" src="https://github.com/user-attachments/assets/ffa821c3-2046-4604-b089-817a769bba7f" />

3. htop : user friendly, color coded interface that shows real time system monitoring tool and list all process.

   <img width="1034" height="473" alt="image" src="https://github.com/user-attachments/assets/de2ba2bd-b7cb-4bd5-b9d6-d4a30c4313ef" />

# Service Checks : 
1. systemctl status <service_name> : his provides detailed information, including whether it is active, inactive, or failed, and recent log entries.

   <img width="1023" height="411" alt="image" src="https://github.com/user-attachments/assets/01b47049-ca1a-482a-8c18-8dddd76cfa96" />

2. systemctl list-units --type=service --state=active : This command list all active services.

    <img width="1090" height="485" alt="image" src="https://github.com/user-attachments/assets/48076fc3-94ce-4640-a904-7d40e24fb905" />

3. systemctl enable <service_name> : configures a service to start automatically when the system boots.

   <img width="1380" height="127" alt="image" src="https://github.com/user-attachments/assets/a143d59b-ee5b-46c9-bf44-0bfe9b0920ae" />

# Log Checks : 
1. journalctl -u <service_name> : This command shows log of specific service manage by systemd.

   <img width="1011" height="290" alt="image" src="https://github.com/user-attachments/assets/00f75d83-06ee-4c56-a477-3066d22eaee2" />

2. sudo journalctl -u <service_name> -f : this command shows real time log of specific service.

   <img width="1478" height="370" alt="image" src="https://github.com/user-attachments/assets/b20ef4b7-7cd1-4c27-bea8-d1dd6570fcbd" />

3. tail -n 50 <file_name> : This command shows the last 50 lines of a file.

   <img width="1049" height="343" alt="image" src="https://github.com/user-attachments/assets/beb89020-e726-4b5e-a4e7-6b0958c0c66f" />

 4. tail -f /var/log/syslog : This command shows live system log.

    <img width="1023" height="450" alt="image" src="https://github.com/user-attachments/assets/cb8a2100-dbfa-4afd-bd12-db861a0959ae" />

# Troubleshoot nginx service: 
1. sudo systemctl status nginx : Check status of nginx service active or inactive.

   <img width="1090" height="346" alt="image" src="https://github.com/user-attachments/assets/0bc322fd-d210-478d-a273-065918f538e0" />

2. sudo systemctl start nginx : if nginx service status is inactive then start this service and check status. 

   <img width="963" height="416" alt="image" src="https://github.com/user-attachments/assets/63d7fe66-3e05-47f3-8bc0-c64f2d2c5b05" />
 
3. sudo systemctl enable nginx : enable nginx service start service automatically after boot.

   <img width="1090" height="122" alt="image" src="https://github.com/user-attachments/assets/c54bfe37-c187-4e4b-8593-a13aa620d99c" />


