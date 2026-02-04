## Users & Group Created:
1. Users : Tokyo, berlin, professor, nairobi.
2. Groups : developers, admins, project-team.

## Group assignment who is in the groups:
1. developers group : Tokyo, berlin.
2. admis group : berlin, professor.
   <img width="1090" height="230" alt="image" src="https://github.com/user-attachments/assets/d679abd5-1ce9-466f-8896-c0d38992e5ca" />
3. project-team : nairobi, Tokyo.
   <img width="883" height="237" alt="image" src="https://github.com/user-attachments/assets/20be423f-6de8-474d-828e-561fb1f08144" />

## Directory Created: 
1. create a directory dev-project in /opt directory and assign this directory to developer group
   <img width="1048" height="184" alt="image" src="https://github.com/user-attachments/assets/ac96fdd1-29fc-4ef0-a579-d55b0a8e021c" />
2. create a directory "/opt/team-workspace" and assign to group "project-team"
   <img width="1090" height="281" alt="image" src="https://github.com/user-attachments/assets/e081527e-4d02-4e73-80a1-7e2574dcef0e" />
   <img width="973" height="245" alt="image" src="https://github.com/user-attachments/assets/16317e89-1311-4eb1-9d68-17a99b89b749" />

## Commands used in this task
1. sudo useradd -m "username" : create a new user use '-m' option for create home directory of user in /home
   <img width="1090" height="209" alt="image" src="https://github.com/user-attachments/assets/b7390bb6-da9f-41e9-9727-5edfd29a5c2d" />
2. cat /etc/passwd : verify users in system.
    <img width="1090" height="210" alt="image" src="https://github.com/user-attachments/assets/dfb82c87-46c6-4572-8b45-fad95f55548a" />
3. sudo groupadd "groupname" : Create a new group.
   <img width="1023" height="221" alt="image" src="https://github.com/user-attachments/assets/023e4831-a8ec-4788-bce9-4566a7c8147f" />
5. cat /etc/group : verify groups in system.
   <img width="1056" height="241" alt="image" src="https://github.com/user-attachments/assets/7ef50c8e-cb07-419c-a1ae-21b93bb24584" />
6. sudo usermod -aG "Groupname" "username" : add user in to a group.
   <img width="1044" height="289" alt="image" src="https://github.com/user-attachments/assets/54bd291e-c83c-4720-8aa1-d4edea230615" />
7. sudo chown :groupname "file or directorypath" : assign a directory or file to group using chown command for assign ownership of that file and directory to that group.
 <img width="1048" height="184" alt="image" src="https://github.com/user-attachments/assets/6b41449f-7ec3-4bc5-a044-3740d01b0e3c" />
8. sudo chmod 775 "pathofdirectoryorfile" : use to add/edit read write execute permission of file or directory.
  <img width="1006" height="415" alt="image" src="https://github.com/user-attachments/assets/cf7f2467-9de1-437b-9462-0909ea3640b7" />

## Outcome:
1. user management add user assign group.
2. create a directory set permissions of directory assign group to directory
3. setGid (set group ID) Any new file or folder created inside it automatically gets the same group as the parent folder. 
   sudo chmod 2775 /opt/dev-project
 


