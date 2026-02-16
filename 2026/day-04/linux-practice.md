----------------------------------------       Linux Practice Day-04    ----------------------------------------------------------

Run and record output for **at least 6 commands**
- Include **2 process commands** (`ps`, `top`, `pgrep`, etc.)

- ps : shows running process for current terminal only 

    <img width="288" height="65" alt="image" src="https://github.com/user-attachments/assets/877026b3-c683-4ed7-8578-0e3382cb6d0f" />

- ps -ef : shows all system running process
      <img width="615" height="442" alt="image" src="https://github.com/user-attachments/assets/849dfef0-7b3e-4101-b329-ccff29177f6c" />
- top : shows live real-time running process
- difference between ps aux and top is "ps aux" shows a snapshot of running process doesn't auto refresh
- ps is good for scripting and top is good for monitoring
  <img width="930" height="284" alt="image" src="https://github.com/user-attachments/assets/a802eb97-ea15-4159-8e5f-c619cdd97dfd" />

-pgrep : used to find the process IDs (PIDs) of running processed by name or other attributes:
- ubuntu@ip$  "pgrep nginx"
- ubuntu@ip$  "pgrep -l nginx ": Shows PID + process name
- ubuntu@ip$  "pgrep -c nginx" : returns numbers of running nginx processes
 
 

   <img width="327" height="86" alt="image" src="https://github.com/user-attachments/assets/2c2bf332-0d2a-436d-9200-a5b1581e094a" />
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Service commands** (`systemctl status`, `systemctl list-units`, etc.)

- systemctl status nginx:

  <img width="960" height="269" alt="image" src="https://github.com/user-attachments/assets/bbf6b164-5b6b-44d6-b66d-4e2a84a6098a" />

- systemctl list-units : it showns currently active loaded units managed by systemd ( Active service, mounted filesystems , sockets, timers,etc )

	 <img width="1325" height="493" alt="image" src="https://github.com/user-attachments/assets/c1b797c5-04af-45e1-8414-6783e1bf3c1d" />

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Log commands (`journalctl -u <service>`, `tail -n 50`, etc.)

- journalctl -u nginx 
    
  <img width="955" height="183" alt="image" src="https://github.com/user-attachments/assets/bb588892-dfbe-4e30-9e81-3ea38c387b72" />

- "tail -n 50 /var/log/nginx/access.log"  or  "tail -n 50 /var/log/nginx/error.log" : It shows most recent 50 log entries.

	 <img width="1324" height="186" alt="image" src="https://github.com/user-attachments/assets/9d9588a8-2681-4887-a6d5-d4d9db080180" />

- Less command : " less /var/log/syslog "
- Grep : " grep -i error /var/log/syslog "
- " tail -f app.log | grep ERROR " :
- tail for real-time monitoring |  grep for filtering  | Less is used to view Large log safely | Log files are typically stored in var/logs

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Pick **one service on your system** (example: `ssh`, `cron`, `docker`) and inspect it

Most common production troubleshooting starts with below commands 
- systemctl status service-name
- systemctl is-enabled service-name
- journalctl -u service-name -n 20
- ps -ef | grep service-name
- sudo ss -tulnp | grep service-name
- sudo ss -tulnp | grep :portnumber (where :80 represnts port number)

	 <img width="1063" height="622" alt="image" src="https://github.com/user-attachments/assets/28387433-bb16-4f01-8a6e-a212c47fb13f" />


Nginx Troubleshooting: 

Installed nginx : with 
- sudo apt install nginx -y
- sudo systemctl start nginx
- exposed port 80 of Ec2 instance to my IP but still web-page was not up.
- So tried to troubleshoot it with follwing commands :
- sudo systemctl restart nginx :
  this should fix the issue and if not try below and see if all are giving responses.
- sudo systemctl status nginx : you should see response like this :
    Active: active (running) since Mon 2026-02-16 02:54:00 UTC; 9min ago

- to check port 80 is listening actively : sudo ss -tulnp | grep :80
  Response should be like this:
  
  tcp   LISTEN 0      511              0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=1809,fd=5),("nginx",pid=1808,fd=5),("nginx",pid=1806,fd=5))
  tcp   LISTEN 0      511                 [::]:80           [::]:*    users:(("nginx",pid=1809,fd=6),("nginx",pid=1808,fd=6),("nginx",pid=1806,fd=6))

- check in ec2 instance , you should get an html response:
  ubuntu@ip-172-31-31-60:~$ curl http://localhost
  Response: <!DOCTYPE html>
  <html>
  <head>
  <title>Welcome to nginx!</title>
  <style>
   html { color-scheme: light dark; }
   body { width: 35em; margin: 0 auto;
   font-family: Tahoma, Verdana, Arial, sans-serif; }
  </style>
  </head>
