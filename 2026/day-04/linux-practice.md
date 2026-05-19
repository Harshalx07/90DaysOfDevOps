Day 04 – Linux Practice: Processes and Services
Overview

Today I practiced basic Linux commands related to processes, services, and logs on my Ubuntu EC2 instance.
I explored running processes, checked system services, and reviewed system logs for troubleshooting.

Process Checks
1. Checking All Running Processes
Command
ps aux
Purpose

Used to display all currently running processes in the system.

Screenshot
![ps aux](./Screenshot%202026-05-19%20at%2010.43.37%E2%80%AFAM(2).png)
2. Checking Top CPU Consuming Processes
Command
ps aux --sort=-%cpu | head -10
Purpose

Displays top CPU consuming processes.

Screenshot
![Top CPU Processes](./Screenshot%202026-05-19%20at%2010.44.34%E2%80%AFAM(1).png)
3. Monitoring Live System Processes
Command
top -bn1 | head -20
Purpose

Used to monitor system resource usage like CPU and memory.

Screenshot
![top command](./Screenshot%202026-05-19%20at%2010.45.46%E2%80%AFAM(1).png)
4. Finding SSH Process
Command
pgrep sshd
Purpose

Used to find the process ID of the SSH service.

Screenshot
![pgrep sshd](./Screenshot%202026-05-19%20at%2010.46.27%E2%80%AFAM(1).png)
Service Checks
5. Checking SSH Service Status
Command
systemctl status ssh
Purpose

Used to inspect the current state of the SSH service.

Observation

The SSH service was inactive during the check.

Screenshot
![SSH Status](./Screenshot%202026-05-19%20at%2010.47.05%E2%80%AFAM(1).png)
6. Listing Running Services
Command
systemctl list-units --type=service --state=running
Purpose

Displays all currently running services.

Screenshot
![Running Services](./Screenshot%202026-05-19%20at%2010.47.39%E2%80%AFAM(1).png)
Log Checks
7. Viewing SSH Logs
Command
journalctl -u ssh --since today
Purpose

Used to check SSH related logs and login activity.

Observation

I observed SSH startup logs and successful login entries.

Screenshot
![SSH Logs](./Screenshot%202026-05-19%20at%2010.49.24%E2%80%AFAM(1).png)
8. Checking Nginx Logs
Command
journalctl -u nginx -n 30
Purpose

Attempted to check Nginx logs.

Observation

No entries were found because Nginx service was not running.

Screenshot
![Nginx Logs](./Screenshot%202026-05-19%20at%2010.50.54%E2%80%AFAM(1).png)
9. Viewing System Logs
Command
sudo tail -n 50 /var/log/syslog
Purpose

Displays the latest system log entries.

Observation

I observed cron jobs, package services, and temporary cleanup activities.

Screenshot
![Syslog](./Screenshot%202026-05-19%20at%2010.52.21%E2%80%AFAM.png)
10. Monitoring Live System Logs
Command
sudo tail -f /var/log/syslog
Purpose

Used to monitor system logs in real time.

Screenshot
![Live Syslog](./Screenshot%202026-05-19%20at%2010.54.01%E2%80%AFAM.png)
11. Searching Failed Authentication Logs
Command
sudo grep "Failed" /var/log/auth.log
Purpose

Used to search failed login attempts in authentication logs.

Observation

No failed login attempts were found.

Screenshot
![Auth Logs](./Screenshot%202026-05-19%20at%2010.54.35%E2%80%AFAM.png)
Mini Troubleshooting Steps
Service Inspected: SSH
Steps Performed
Checked SSH process using:
pgrep sshd
Verified SSH service status:
systemctl status ssh
Reviewed SSH logs:
journalctl -u ssh --since today
Checked authentication logs:
sudo grep "Failed" /var/log/auth.log
What I Learned
How to inspect running processes
How to check service health using systemctl
How to inspect logs using journalctl and tail
Basic troubleshooting workflow for Linux services
Commands Practiced
ps aux
ps aux --sort=-%cpu | head -10
top -bn1 | head -20
pgrep sshd
systemctl status ssh
systemctl list-units --type=service --state=running
journalctl -u ssh --since today
journalctl -u nginx -n 30
sudo tail -n 50 /var/log/syslog
sudo tail -f /var/log/syslog
sudo grep "Failed" /var/log/auth.log