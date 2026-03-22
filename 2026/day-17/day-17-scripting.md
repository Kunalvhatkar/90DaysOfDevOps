# Shell Scripting: Loops, Arguments & Error Handling

## Task 1: For Loop

a.	Create shell scripting use for loop for print fruit names. 
    <img width="846" height="221" alt="image" src="https://github.com/user-attachments/assets/31062ad0-6fc5-4c3c-9682-c7917e80fb6e" />
    <img width="960" height="248" alt="image" src="https://github.com/user-attachments/assets/1e076161-3219-486f-8d01-ad7cc4d08dcd" />

b.	Create count.sh that: Prints numbers 1 to 10 using a for loop  
    <img width="626" height="276" alt="image" src="https://github.com/user-attachments/assets/ed30f8aa-088d-44c9-9170-14ae3a7bc281" />
    <img width="963" height="54" alt="image" src="https://github.com/user-attachments/assets/5d3cf839-1afb-49a5-b5c4-31c35fe05431" />
    <img width="969" height="366" alt="image" src="https://github.com/user-attachments/assets/732a0fe7-ddee-4293-979b-f0fa42f81c83" />

## Task 2: While Loop
 1.	Create countdown.sh that:
    
    •	Takes a number from the user
   	
    •	Counts down to 0 using a while loop

   	•	Prints "Done!" at the end
   	
   	<img width="1018" height="359" alt="image" src="https://github.com/user-attachments/assets/db7bae7b-7a9d-4d51-b41f-5e54023ae75f" />
    <img width="991" height="403" alt="image" src="https://github.com/user-attachments/assets/de001f73-d51b-4509-a4cc-dfe646a0ba0e" />

## Task 3: Command-Line Arguments 
1.	Create greet.sh that:
   
  •	Accepts a name as $1

  • Prints Hello, <name>!
  
  •	If no argument is passed, prints "Usage: ./greet.sh "

   <img width="1090" height="225" alt="image" src="https://github.com/user-attachments/assets/1281bfb3-7436-4f7c-81ad-efa806213f5e" />
   <img width="1090" height="163" alt="image" src="https://github.com/user-attachments/assets/cd58aed7-84dd-4e28-af4e-cb193026ae4d" />

2.	Create args_demo.sh that:
   
  • Prints total number of arguments ("$#")

  • Prints all arguments ($@)
  
  • Prints the script name ($0)

  <img width="1090" height="491" alt="image" src="https://github.com/user-attachments/assets/99b2fdd1-0d5f-460b-9d0c-b37f392eda86" />
  <img width="1090" height="139" alt="image" src="https://github.com/user-attachments/assets/66e78f45-6d22-4fe3-8179-2c681d9e52ee" />
  <img width="840" height="151" alt="image" src="https://github.com/user-attachments/assets/5686ae97-dfd3-4fdd-91a7-fa4e537c994f" />

##  Task 4: Install Packages via Script: 
1. Create install_packages.sh that:
   
  • Defines a list of packages: nginx, curl, wget
  
  • Loops through the list
  
  • Checks if each package is installed (use dpkg -s or rpm -q)
  
  • Installs it if missing, skips if already present
  
  • Prints status for each package
  
  • Run as root: sudo -i or sudo su

   <img width="996" height="676" alt="image" src="https://github.com/user-attachments/assets/37776454-54a3-4b82-a19c-5562b9ebf6f0" />

   <img width="1019" height="260" alt="image" src="https://github.com/user-attachments/assets/223943bd-307a-4462-88af-1742e884a901" />

## Task 5: Error Handling
1.	Create safe_script.sh that:
   
  • Uses set -e at the top (exit on error)
  
  • Tries to create a directory /tmp/devops-test
  
  • Tries to navigate into it
  
  • Creates a file inside
  
  • Uses || operator to print an error if any step fails

  <img width="964" height="409" alt="image" src="https://github.com/user-attachments/assets/42b4ca68-04dc-4e75-98bc-57082c6bbce1" />

  <img width="985" height="110" alt="image" src="https://github.com/user-attachments/assets/b297d5d2-38ce-4a36-b63f-7713b5025135" />
  
  <img width="994" height="127" alt="image" src="https://github.com/user-attachments/assets/7ca035ec-8dfe-4871-9e6d-fa3289c4f968" />

2.	Modify your install_packages.sh to check if the script is being run as root — exit with a message if not.
   
   <img width="953" height="734" alt="image" src="https://github.com/user-attachments/assets/dc063d69-c655-4d75-a8b5-01dc80146c2d" />
   
   <img width="943" height="59" alt="image" src="https://github.com/user-attachments/assets/5e8f8338-1fcd-400f-83bf-f7a026a8ca1c" />

   <img width="954" height="170" alt="image" src="https://github.com/user-attachments/assets/0c4d904e-3530-437d-93f2-23a91577567a" />






