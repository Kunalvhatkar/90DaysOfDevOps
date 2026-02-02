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
10. htop :  realtime system monitoring and process viewer.

# File Management: 
1. touch : Create new file.
2. touch -t : change timestamp of file.
3. rm : remove file. we use "*" option to remove all files in same extension at a time ex: rm *.txt (remove all .txt files)
4. rm -rf : remove file "-r"recursive and "f"force.
5. cp source target : copy file. example cp file1 file2.copy
6. cp -r sourcedirectory targetdirectory : copy complete derectory."-r"copy all files in directory recursive.
7. mv : rename file or move file to another directory.
8. head : use display first 10 lines in file by default display first 10 lines. user can customize line number ex: head -5 file.txt.
9. tail :  display last 10 lines of file. user can customize line number ex: tail -6 file.txt.

