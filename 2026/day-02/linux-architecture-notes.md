# Day 02 – Linux Architecture, Processes, and systemd
You will create a short note that explains:
- The core components of Linux (kernel, user space, init/systemd)
  Linux Kernel: Kernel is the core heart of the Linux system which manages communication between hardware and software.

- User Space: User space is a palce where your program exist

- init/systemd: this is the first procees after the linux kernel boots up 
            kernel -> starts PID 1 ( this is init /systemd)
            PID 1 process= init system

- How processes are created and managed?
  Linux uses parent and child model.
  Running : On CPU right now 
  Runnable: Ready waiting  for CPU 
  sleeping: Waiting for I/O or event 
  stopped: Paused
  Zombie: Finished, waiting ( when process ends 
  kernel keeps its exit status 
  It becomes a zombie)
  
- What systemd does and why it matters
  systemd is the manager of everything that runs on linus system once the kernel starts.
  Linux-> is a city
  systemd -> is the city operator.
------------------------------------------------------------------------------------
- List **5 commands** you would use daily
  cd /user/downloads/abc.txt
  ls : list out the files and directoires 
  ps aux  | grep nginx 
  top : shows real time system activity - running process , CPU, memory 
  htop : human friendly top 
  systemctl: with this you can check start, stop, check, and manage system services
  like
  systemctl start nginx
  systemctl stop nginx
  systemctl reboot 
  systemctl list-units --type=service -> show running services
---------------------------------------------------------------------------