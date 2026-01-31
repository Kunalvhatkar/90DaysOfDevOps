# Linux Architecture: 
## Application or User space: 
1.user gives commands to the system for perform some task. 
         
##  Shell:
1. its an a software and interface to the kernel
2. Shell takes commands from the user and interprets them.
3.shell transmits these commands to the kernel, which then performs the requested operations.

##  Kernel:
1. is an core of linux operating system. directly talk with hardware.
2. managing memory,process scheduling,device drivers, and file systems.
## Hardware : 
1. lowest level of linux operating system.
2.It includes device drivers, memory management, CPU control and I/O operations

## Visual representation
<img width="512" height="400" alt="linux architecture" src="https://github.com/user-attachments/assets/80d8fc3a-5b4c-455d-90d4-2a64f983d77e" />

# How processes are created and managed
1.user runs command.
2.Shell receives command.
3.shell sends request to kernel.(create a new process)
4.kernel creates process: 
      (a) creates a new process entry.
      (b)Assign a PID(Process ID).
      (c)Allocate memory.
      (d)loads program into RAM.
5.Now process exists.

## Process States:
1. R = Running
2. S = Sleeping
3. D = Waiting for disk
4. T = Stopped
5. Z = Zombie(finished but not cleaned)

## Process Management in linux:
1. top = Live process monitor.
2. htop
3. ps = show running process.
4. ps aux = Show all processes.(PID, User, CPU usage, Memory usage, Command name)
5. kill PID = Kill process 


# What is Systemd?:
1.Is the default system and service manager used in linux operating system.
2.It act as the first process(PID 1) during boot.

# Linux command 
1. pwd = present working directory.
2. whoami = user name.
3. man = manual of any command.
4. ls = listing file and directories. 
5. cd = change directory
6. mkdir = create a new directory
 
