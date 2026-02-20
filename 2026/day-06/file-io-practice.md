# Day 06 – Linux Fundamentals: Read and Write Text Files
## Create a file named notes.txt using "touch" command : 
 <img width="806" height="134" alt="image" src="https://github.com/user-attachments/assets/4fa05999-8c1d-4f24-948a-3b123034828e" />

## Write a lines into the file using redirection (> and >>)
a. echo  “Line 1” > notes.txt : write a line in file. <img width="910" height="170" alt="image" src="https://github.com/user-attachments/assets/103022e4-a7a0-490b-8fdc-60507c295ba6" />

b. echo “Line 2” >> notes.txt : appends the text "Line 2" as a new line to the end of the file. <img width="844" height="175" alt="image" src="https://github.com/user-attachments/assets/2fe03bf8-187a-49c8-905c-dd0db0a69598" />

c. echo "Line 3" | tee -a notes.txt : is used to add new text to a file while simultaneously seeing that text in terminal.  <img width="926" height="226" alt="image" src="https://github.com/user-attachments/assets/3223c366-547f-4177-bc9f-bf4d04a5a986" />

 ## Read the full file using "cat" command: 
 <img width="654" height="176" alt="image" src="https://github.com/user-attachments/assets/c075cfb9-f8c7-41dc-8ee5-50483a579518" />

## Use head and tail to read parts of the file: 
a. head -4 notes.txt : used to read first four lines of file. <img width="740" height="184" alt="image" src="https://github.com/user-attachments/assets/ffadd825-1b60-4e9f-b92b-69cc29218c2f" />

b. tail -4 notes.txt : used to read last four lines of file.  <img width="751" height="175" alt="image" src="https://github.com/user-attachments/assets/84f4522e-4893-43f7-9b91-77fce6a1a457" />
