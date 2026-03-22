# Shell Scripting: Functions & intermediate Concepts

## Task 1: Basic Functions
   Create functions.sh with:
   1. A function greet that takes a name as argument and prints Hello, <name>!
   2. A function add that takes two numbers and prints their sum
   3. Call both functions from the script

<img width="684" height="510" alt="image" src="https://github.com/user-attachments/assets/16d77173-bd9f-48ef-916e-5a31cef50b97" />

<img width="1090" height="99" alt="image" src="https://github.com/user-attachments/assets/00d4af3a-7310-44c2-a979-47ec389d1b56" />

## Task 2: Functions with Return Values
   Create disk_check.sh with:
   1. A function check_disk that checks disk usage of / using df -h
   2. A function check_memory that checks free memory using free -h
   3. A main section that calls both and prints the results

   <img width="1090" height="398" alt="image" src="https://github.com/user-attachments/assets/d3046ef3-a9c3-41f5-a8d7-57a128c9e043" />

   <img width="1090" height="411" alt="image" src="https://github.com/user-attachments/assets/c819ba80-ea8f-45a4-b74b-5ca76a7efefd" />

## Task 3: Strict Mode — set -euo pipefail
   Create strict_demo.sh with set -euo pipefail at the top
   1. Try using an undefined variable — what happens with set -u? 
   2. Try a command that fails — what happens with set -e?
   3. Try a piped command where one part fails — what happens with set -o pipefail?
      <img width="1090" height="643" alt="image" src="https://github.com/user-attachments/assets/c400b775-cea5-4fc0-bc68-30e7016884c8" />

## Task 4: Local Variables
   Create local_demo.sh with:
   1. A function that uses local keyword for variables
   2. Show that local variables don't leak outside the function
   3. Compare with a function that uses regular variables
   <img width="1159" height="721" alt="image" src="https://github.com/user-attachments/assets/4865df01-b901-4011-a090-2d24c2baca52" />
   <img width="1090" height="266" alt="image" src="https://github.com/user-attachments/assets/22c053d3-ab92-4745-bc37-842505c1904c" />

## Task 5: Build a Script — System Info Reporter
   Create system_info.sh that uses functions for everything:
   1. A function to print hostname and OS info
   2. A function to print uptime
   3. A function to print disk usage (top 5 by size)
   4. A function to print memory usage
   5. A function to print top 5 CPU-consuming processes
   6. A main function that calls all of the above with section headers
   7. Use set -euo pipefail at the top
   <img width="1063" height="1159" alt="image" src="https://github.com/user-attachments/assets/230249eb-89be-4de0-b2a8-073bafd9de47" />
   <img width="1090" height="811" alt="image" src="https://github.com/user-attachments/assets/0a453811-ed8a-4ecd-ba4f-511df8a761a9" />

  
