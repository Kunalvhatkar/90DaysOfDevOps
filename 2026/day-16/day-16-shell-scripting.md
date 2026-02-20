# Day 16 – Shell Scripting Basics

## Task 1: Your First Script

1.	Create a file hello.sh : vim hello.sh 
2.	Add the shebang line #!/bin/bash at the top

  	<img width="624" height="123" alt="image" src="https://github.com/user-attachments/assets/bc0223a2-fc8f-4cd1-8e10-99459db459ce" />

4.	Print Hello, DevOps! using echo
5.	Make it executable and run it 

  	<img width="990" height="240" alt="image" src="https://github.com/user-attachments/assets/c3544991-c13b-44d4-9bf8-dd8fbeeea6dc" />

6.	Remove shebang “#!/bin/bash” and execute the script

  	<img width="440" height="150" alt="image" src="https://github.com/user-attachments/assets/272a0f18-2566-42a7-a240-7362f1472e0e" />

  	<img width="878" height="126" alt="image" src="https://github.com/user-attachments/assets/3710ce33-6cac-4f5d-9484-1c6f0d14af68" />

### What I learn : 
After removing shebang “#!/bin/bash” from script doesn't any impact on execution of script. script run properly and give proper output.

## Task 2: Variables
1.	Create variables.sh with:
 * A variable for your NAME
 * A variable for your ROLE (e.g., "DevOps Engineer")
 * Print: Hello, I am NAME and I am a ROLE
   
  <img width="801" height="296" alt="image" src="https://github.com/user-attachments/assets/57f8bf3e-a265-4867-987d-afd4ae34159d" />
  
  <img width="878" height="196" alt="image" src="https://github.com/user-attachments/assets/05e59f3f-924f-4d17-9517-3b308aeced4c" />

  * Use single quotes on echo ‘statement’ print statements not variable value. 
  
  <img width="865" height="275" alt="image" src="https://github.com/user-attachments/assets/379c4d88-49d9-48c0-ad8d-981ac02599a7" />

  <img width="915" height="106" alt="image" src="https://github.com/user-attachments/assets/d5a10875-7edf-4b9b-a1eb-b6019a5c5884" />

 ## Task 3: User Input with read 
 1.	Create greet.sh that:
   * Asks the user for their name using read
   * Asks for their favourite tool
   * Prints: Hello name, your favourite tool is tool
   
   <img width="930" height="256" alt="image" src="https://github.com/user-attachments/assets/74673188-65f6-4183-a0f4-af2e5ab48cfb" />

   <img width="973" height="204" alt="image" src="https://github.com/user-attachments/assets/cba9c775-2d04-47fc-ab85-e923edfca6e2" />

## Task 4: If-Else Conditions
1.	Create check_number.sh that:
   •	Takes a number using read
   •	Prints whether it is positive, negative, or zero  

  	<img width="771" height="534" alt="image" src="https://github.com/user-attachments/assets/13eb7f83-eadf-4ce9-bdb7-f62c15d6195b" />

  	<img width="946" height="386" alt="image" src="https://github.com/user-attachments/assets/66c9c11e-a860-46b2-838e-78e8ce1bd200" />

2.	Create file_check.sh that:
   •	Asks for a filename
   •	Checks if the file exists using -f
   •	Prints appropriate message 

  	<img width="903" height="434" alt="image" src="https://github.com/user-attachments/assets/bb95ebba-21f9-4294-89ae-1a88f4fcbc3c" />

  	<img width="936" height="271" alt="image" src="https://github.com/user-attachments/assets/f12656e7-c423-4268-b000-b8d5641919c3" />

## Task 5: Combine It All
1. Create server_check.sh that:
   •	Stores a service name in a variable (e.g., nginx, sshd)
   •	Asks the user: "Do you want to check the status? (y/n)"
   •	If y — runs systemctl status <service> and prints whether it's active or not
   •	If n — prints "Skipped."

   <img width="994" height="613" alt="image" src="https://github.com/user-attachments/assets/730b8605-7810-4aa1-b0f4-05ed755a3047" />

   <img width="990" height="234" alt="image" src="https://github.com/user-attachments/assets/60b90823-f4cb-4d5c-8393-b48b844e1674" />

