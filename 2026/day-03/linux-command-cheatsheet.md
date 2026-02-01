# Process Management Command:
1. ps : list all runing process.
2. ps -e : list all process currently running with additional information about process.
3. ps -ef : list all running process with full format.
4. ps -eF : list all running process with more details.
5. ps -ely : listing all process with long format. "-y" is not show flag and only use wit "-l" option.
6. ps -U root -u root u : Show processes owned by user root.Display in user-oriented format (nice, detailed layout).
7. ps -eo euser,ruser,suser,fuser,f,comm,label : see every process with a user defined format.Custom output format (you choose columns).
8. ps axo stat,euid,ruid,tty,tpgid,sess,pgrp,ppid,pid,pcpu,comm : (a = Show processes from all users) (x = Show processes without a terminal (background/system)) (o = Custom output format)
9. top : display running process.CPU usage,Memory usage,Load average.

# File Management: 
1. touch : Create new file.
2. touch -t : change timestamp of file.
3. rm : remove file.
4. 
