# Day 10 Challenge

## Files Created:
1. Create file devops.txt using touch command <img width="999" height="284" alt="image" src="https://github.com/user-attachments/assets/5f931be0-70a8-4e7d-9934-e8afc533aca5" />
2. Create a newfile.txt using echo command  <img width="1065" height="225" alt="image" src="https://github.com/user-attachments/assets/add8c957-970b-470d-918d-56b00160e70d" />
3. Create text file myfile.txt using cat command <img width="1018" height="656" alt="image" src="https://github.com/user-attachments/assets/e07557d9-5c8e-4298-9af0-f340d1311ee7" />
4. Create script.sh using vim
   
   <img width="663" height="145" alt="image" src="https://github.com/user-attachments/assets/787f8dca-4f10-4fe0-ba4a-69fc49e3205c" />

   Write a script echo “Helloo DevOps” save and quite esc + wq. 

   <img width="734" height="239" alt="image" src="https://github.com/user-attachments/assets/a2a14998-fd32-4962-9626-2c0d07c331a9" />
6.	Check all create file permission using ls -l command <img width="1010" height="359" alt="image" src="https://github.com/user-attachments/assets/a1ae5fd5-b9fa-4952-862d-02c5227b4105" />

## Permission Changes
1. Check permissions of devops.txt myfile.txt newfile.txt script.sh <img width="1011" height="181" alt="image" src="https://github.com/user-attachments/assets/fda6a704-060a-4b74-8a39-2eaf7636f4f5" />
2. Added executable permission in Script.sh. 
  a. Method 1 (+x) :  chmod +x script.sh <img width="929" height="229" alt="image" src="https://github.com/user-attachments/assets/6a0ce984-35c9-4d00-82cf-3c50e402d566" />
  b. Method 2 (give all permissions to all): chmod 777 script.sh <img width="896" height="226" alt="image" src="https://github.com/user-attachments/assets/553d0801-d463-4b83-912d-c7a186f782e3" />
  c. Run script

     <img width="720" height="189" alt="image" src="https://github.com/user-attachments/assets/c0ffe9c4-f141-402f-8d50-0e60e81a4438" />
4. Set devops.txt read only (remove write for all)  <img width="919" height="215" alt="image" src="https://github.com/user-attachments/assets/28594160-fec7-487a-8f99-3805bccc12e6" />
5. Set newfile.txt to 640 (owner: rw, group: r, others: none)  <img width="939" height="290" alt="image" src="https://github.com/user-attachments/assets/68ec29d9-aff3-4cde-bbd3-f50bb506ad86" />
6. Create directory project/ with permissions 755 <img width="1008" height="346" alt="image" src="https://github.com/user-attachments/assets/65886c35-19f4-43fd-bd50-1a2f78b64329" />
7. Check deirectory permissions <img width="990" height="109" alt="image" src="https://github.com/user-attachments/assets/e22de7ec-deb3-4dad-a7af-7b589279e007" />

## Commands Used
1. touch, echo, cat and vim command for creates a text and script file.
2. ls -l and ls -ld commands for check permissions of files.
3. chmod command foe change permission.
4. mkdir -m 755 project create a directory with permission. Specify permission explicitly upon creation of directory <img width="1008" height="346" alt="image" src="https://github.com/user-attachments/assets/eb419dfa-70d3-499d-a4cc-8c96e0f6e00d" />

## 🚀 What I learned
1. Permissions of file based on user like owner, Group, Other.
2. how to set a permissions of files.
3. I try write a contain in file but file have read only permission  <img width="1038" height="656" alt="image" src="https://github.com/user-attachments/assets/c5644a11-b47f-4f0a-9611-8bf7866ab88e" />

