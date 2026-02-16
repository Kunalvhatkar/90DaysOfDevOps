# Day 11 Challenge File Ownership

## Files and Directory Created 
1. Create devops-file.txt and check its permission, owner and group.  <img width="1019" height="210" alt="image" src="https://github.com/user-attachments/assets/95ca1b44-297d-4bea-bddd-e5c9d12793a3" />
2. Create teams-notes.txt and check its Group. <img width="877" height="323" alt="image" src="https://github.com/user-attachments/assets/de18c67c-6ae1-4461-aeea-22a2a435fb45" />
3. Create file project-config.yaml and check its owner and group.  <img width="1017" height="184" alt="image" src="https://github.com/user-attachments/assets/268fe2f3-2861-4e13-b4c5-766faf3785ee" />
4. Create directory “app-logs/” and check owner and group.  <img width="1034" height="139" alt="image" src="https://github.com/user-attachments/assets/0148b5ba-f324-4428-9d2e-4dff44df5b83" />
5. Create directory structure: a. heist-project/vault  b. heist-project/plans <img width="1033" height="295" alt="image" src="https://github.com/user-attachments/assets/1313d63f-9fff-4972-be77-f05490aeb215" />
6. Create file in directory: a. heist-project/vault/gold.txt  b. heist-project/plans/strategy.conf  <img width="1013" height="135" alt="image" src="https://github.com/user-attachments/assets/91af392c-622f-4fc9-9dd8-20e090be1d4d" />
                         <img width="698" height="97" alt="image" src="https://github.com/user-attachments/assets/5d790316-1b4f-4bd2-8a31-28af485d5057" /> 
7. Create directory: bank-heist/  <img width="959" height="228" alt="image" src="https://github.com/user-attachments/assets/5ecd3aa4-555b-4075-9fd4-db6c32351fad" />
8. Create 3 files inside: (a) bank-heist/access-codes.txt (b) bank-heist/blueprints.pdf (c) bank-heist/escape-plan.txt <img width="972" height="371" alt="image" src="https://github.com/user-attachments/assets/0551ebfe-4578-4b59-8024-49d199715c99" />

## Ownership Changes : 
1. devops-file.txt change owner to Tokyo. <img width="1028" height="258" alt="image" src="https://github.com/user-attachments/assets/c7092da0-e2d3-4ca1-9e54-7cd2193b9031" />
2. devops-file.txt change owner Tokyo to berlin. <img width="1040" height="308" alt="image" src="https://github.com/user-attachments/assets/b7a9b818-24d3-43d4-a38f-4166c5c51ea8" />
3. Change file group teams-notes.txt group to heist-team. <img width="1015" height="260" alt="image" src="https://github.com/user-attachments/assets/e21adb1c-7011-47d6-8dfa-ff861f614f48" />
4. change owner and group of "project-config.yaml" Change owner to professor AND group to heist-team (one command) <img width="1025" height="130" alt="image" src="https://github.com/user-attachments/assets/1f290e6d-d8ba-487e-9e19-98bffeb441f0" />
5. Change "app-logs/" owner to berlin and group to heist-team. <img width="1002" height="265" alt="image" src="https://github.com/user-attachments/assets/edde2db0-8fc4-4d95-b468-32ec461dab2d" />
6. Change ownership of entire heist-project/ directory: Owner: professor, Group: planners, Use recursive flag (-R) <img width="927" height="237" alt="image" src="https://github.com/user-attachments/assets/c785a1ec-d861-4e21-b90c-ade3eee7f6d8" />
7. Set different ownership:  
(a.) access-codes.txt → owner: tokyo, group: vault-team  <img width="945" height="220" alt="image" src="https://github.com/user-attachments/assets/21ffbcb7-fd40-4074-9256-4d7d4098fed6" />
(b.) blueprints.pdf → owner: berlin, group: tech-team  <img width="975" height="253" alt="image" src="https://github.com/user-attachments/assets/71096e38-12fa-4bb7-a350-fa5fbfe56496" />
(c.) escape-plan.txt → owner: nairobi, group: vault-team  <img width="934" height="260" alt="image" src="https://github.com/user-attachments/assets/03fe3e08-4e4a-4f31-8d8e-cc6eca5f590a" />

## Commands used: 
1. ls -l : Understanding owner and goup. <img width="1046" height="543" alt="chgrp chown ls -l" src="https://github.com/user-attachments/assets/6d08abd1-c46b-469d-84ce-499faa44b485" />
2. chown : change ownership of file and directory. <img width="1028" height="258" alt="image" src="https://github.com/user-attachments/assets/a5565592-c849-476e-a69c-d6c3be40372d" />
3. chgrp : change group of file and directory. <img width="1015" height="260" alt="image" src="https://github.com/user-attachments/assets/7fe9041d-e8c3-4cb6-ad52-a6c80618458f" />
4. chown <owner>:<group> <file_name>: change owner and group in one command. <img width="1025" height="130" alt="image" src="https://github.com/user-attachments/assets/6e6b2e48-8a2d-4c19-a69b-6c71524afb24" />
5. mkdir -p : Create directory structure. <img width="1033" height="295" alt="image" src="https://github.com/user-attachments/assets/ee777eab-46a1-45cb-a6d9-55c9226b5469" />
6. chown -R <owner>:<group> <file_name> : "-R" flag for recursive change owner and group of file or directory. <img width="927" height="237" alt="image" src="https://github.com/user-attachments/assets/1f3e8450-cfea-478a-bfa4-812f5f791398" />
7. ls -lR <directory_name> : Verify all files and subdirectories in directories.   <img width="927" height="509" alt="image" src="https://github.com/user-attachments/assets/85d4b78c-a422-4530-951b-ca6fd3aa4d15" />
