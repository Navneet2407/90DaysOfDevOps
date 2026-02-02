Process Management Commands:

  1. ps :- The ps utility displays a header line, followed by lines containing
     information about all of your processes that have controlling terminals.

  2. top/htop :- Live monitoring of the running processes.

  3. kill :- stop a process

  4. pkill / pgrep : kill or find a process by name.
     for example:  pgrep nginx 
  
  5. lsof: useful for which process is using this file/port
        ex: lsof -p 1234

- File System commands:
  ls, cd, pwd, cat, mkdir, rm, cp, mv, chmod, chown, df, du, find
  ------------------------------------------------------------------------
    6. ls : list out whats here
       ls -l #detailed
       ls -a #show hidden files
       ls -lh #human readable sizes
  -------------------------------------------------  
 7. # prints present working directory
    pwd 

 8. # change directory 
    cd /Downloads/AI/DevOps
    cd .. ( go back to previous directory)
9. # show file content or read file content
    cat file1.txt 
10. Make a directory
    mkdir Devops 

11. # Remove file or directory
     rm abc.txt  #remove file
     rmdir AI    #remove direcotry AI
12. # Create file or diecotry:
     touch nav.txt -> this will create a file 
13. # Copy and Move
    cp fileA fileB
    cp -p file.txt backup.txt ->preserve permission 
14. # Move or rename 
    mv file.txt /Downloads/navneet
    mv oldnname.txt newname.txt
15. # disk usage 
    df -h -> disk free space 
      du -sh * -> directory size 
      du -sh /var/log

16. chmod chnage permission 
    4-> Read
    5-> Read & execute
    6-> Read & write 
    7-> Read write & exe
    chmod 777 abc.txt -> modify the permission of file abc.txt give rwx permission to owner , group , other users.

17. change owner
    chown berlin(user) abc.txt
    chown user:group file.txt

18. head file.txt -> gives top five line from the file
19. tail file.txt -> gives last five lines from the file.

20. Search file
    find /var -name "*.log"


# Importance directories to know:
path       Purpose
/           root
/home      User Files
/etc       config files
/var/log   Logs
/tmp       Temporary files
/usr       System programs

----------------------------------------------------
backup copy :
# cp /etc/nginx/nginx.conf nginx.conf.bak

   











