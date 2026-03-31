<img width="1051" height="201" alt="image" src="https://github.com/user-attachments/assets/b124ac1b-8203-47a1-9ef4-1ae504f32f47" /># Day 22 – Introduction to Git: Your First Repository

## Task 1: Install and Configure Git

1.	Verify Git is installed on your machine  <img width="669" height="119" alt="image" src="https://github.com/user-attachments/assets/8fe78678-b970-4401-9313-b3d9088f714c" />

2.	Set up your Git identity — name and email     <img width="1048" height="100" alt="image" src="https://github.com/user-attachments/assets/66d31e4a-feb6-43e9-b14c-11bd16d4f75c" />

3.	Verify your configuration

   <img width="744" height="104" alt="image" src="https://github.com/user-attachments/assets/e6494139-fd04-4fb4-94e2-bdd947ab5107" />

   <img width="754" height="95" alt="image" src="https://github.com/user-attachments/assets/84ca252f-4329-44f2-baf4-7192e2887c29" />

   <img width="729" height="253" alt="image" src="https://github.com/user-attachments/assets/00f9e760-70bb-4a02-9f62-38703dd945f2" />

## Task 2: Create Your Git Project

1.	Create a new folder called devops-git-practice    <img width="804" height="104" alt="image" src="https://github.com/user-attachments/assets/6c44c2e1-11d9-4c6a-abf9-902164000182" />

2.	Initialize it as a Git repository      <img width="1090" height="335" alt="image" src="https://github.com/user-attachments/assets/ebe91918-2bb4-461e-9e18-97399b44a093" />

3.	Check the status — read and understand what Git is telling you    <img width="994" height="251" alt="image" src="https://github.com/user-attachments/assets/8323c11a-1d87-480f-badd-60265cac6871" />

4.	Explore the hidden .git/ directory — look at what's inside

  	<img width="900" height="185" alt="image" src="https://github.com/user-attachments/assets/1ad40c89-78fe-4518-8a50-c109256b56dc" />

    <img width="959" height="415" alt="image" src="https://github.com/user-attachments/assets/5c350052-8af6-4fb4-9a35-0ffa5c642e89" />

## Task 3: Create Your Git Commands Reference

1.	Create a file called git-commands.md inside the repo   
2.	Add the Git commands you've used so far, organized by category:  
   o	Setup & Config  
   o	Basic Workflow   
   o	Viewing Changes   
3.	For each command, write:   
   o	What it does (1 line)    
   o	An example of how to use it

<img width="1090" height="674" alt="image" src="https://github.com/user-attachments/assets/2e56dfa4-2019-4c20-97aa-4b9f18fad10c" />

## Task 4: Stage and Commit   

1.	Stage your file   <img width="1090" height="351" alt="image" src="https://github.com/user-attachments/assets/3828906e-cf43-46d6-9d6a-a86b5b612bef" />

2.	Check what's staged   <img width="1090" height="351" alt="image" src="https://github.com/user-attachments/assets/8966e0e6-72cf-47d6-a759-6459c4592b48" />

3.	Commit with a meaningful message   <img width="1051" height="121" alt="image" src="https://github.com/user-attachments/assets/811353f1-bdb9-457e-996f-0f44dac88f74" />

4.	View your commit history    <img width="1090" height="225" alt="image" src="https://github.com/user-attachments/assets/dba14b9e-9d92-4ed9-bd74-3a30913632fc" />

## Task 5: Make More Changes and Build History  

1.	Edit git-commands.md — add more commands as you discover them

2.	Check what changed since your last commit
    <img width="1023" height="390" alt="image" src="https://github.com/user-attachments/assets/ec72185e-1f6d-432d-9e4b-3969d7ab68e8" />
    <img width="1016" height="407" alt="image" src="https://github.com/user-attachments/assets/c9346cac-3cc2-4007-8083-c4164341d06f" />

3.	Stage and commit again with a different, descriptive message   <img width="1090" height="130" alt="image" src="https://github.com/user-attachments/assets/8dd033a7-88b5-485d-bf13-6f8e5ee19cef" />

4.	Repeat this process at least 3 times so you have multiple commits in your history

5.	View the full history in a compact format    <img width="1051" height="201" alt="image" src="https://github.com/user-attachments/assets/622d8600-b3ef-44ef-b484-ced23d73a990" />

Task 6: Understand the Git Workflow
Answer these questions in your own words (add them to a day-22-notes.md file):
1.	What is the difference between git add and git commit?   
Answer:    
i.	The git add command moves new or modified files from your working directory to the staging area (also known as the index).   
ii.	The git commit command takes all the changes currently in the staging area and records them as a permanent snapshot in the local Git repository's database.  

2.	What does the staging area do? Why doesn't Git just commit directly?   
Answer:   
i.	The Git staging area (also called the "index") is a temporary draft space where you prepare and review changes before permanently saving them to your project's history.  
ii.	Git doesn’t commit directly because developers need control over what gets committed. The staging area allows us to separate, organize, and verify changes before saving them permanently.  
iii.	If Git committed directly:  
--> All changes would be committed together   
--> Commit history would become messy   
--> It would be harder to track, debug, and review code  

3.	What information does git log show you?  
Answer: git log shows the history of commits in a Git repository. It helps you understand what   changes were made, who made them, and when.  
Information shown by git log:   
i.	Commit Hash :   
     a.  A unique ID for each commit   
     b. Used to identify a specific commit  
     c. Example: a1b2c3d...  
ii.	Author:  Name and email of the person who made the commit
iii.	Date: When the commit was created 
iv.	Commit Message: Description of the changes

4.	What is the .git/ folder and what happens if you delete it?
Answer: The .git/ folder is the hidden directory where Git stores all the information about your repository.
It stores all version control data:
i.	Commits (History): All past commits. Complete project history
ii.	Branches: Information about all branches. Current branch pointer
iii.	Tags: Saved versions/releases
iv.	Configuration: Repository settings (config file)
v.	Objects (Important!): Actual data of files and commits Stored in .git/objects
vi.	HEAD Pointer: Points to the current branch

5.	What is the difference between a working directory, staging area, and repository?  
Answer:   
Working Directory:   
The working directory is the folder on your system where your project files exist and where you write and edit code.   
Staging Area:     
The staging area is a temporary storage area where you select and prepare changes before committing.  
Repository:   
The repository is where Git stores all commits permanently. It is managed inside the hidden .git/ folder.   
