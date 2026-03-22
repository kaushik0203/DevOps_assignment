# DevOps Assignment – System Setup and Automation

## Introduction
The project demonstrates the setup of a secure and monitored development environment which includes system monitoring, user management, and automated backup configuration.

---

## Task 1: System Monitoring Setup

### Tools Used:
- htop
- nmon

### Steps Performed:
- Installed monitoring tools using apt
- Monitored CPU, memory, and processes using htop and nmon
- Checked disk usage using df and du
- Identified high CPU processes using ps command
- Created log file to store system metrics

### Commands Used:
sudo apt update
sudo apt install htop nmon -y
htop
nmon
df -h
du -sh ~
ps aux --sort=-%cpu | head

### Log File:
Stored at:

~/monitoring_logs/report.log

---

## Task 2: User Management and Access Control

### Users Created:
- sarah
- mike

### Steps Performed:
- Created users with passwords
- Created isolated directories:
  - /home/sarah/workspace
  - /home/mike/workspace
- Assigned ownership using chown
- Restricted access using chmod 700
- Set password expiry policy (30 days)

### Commands Used:
sudo adduser sarah
sudo adduser mike
sudo mkdir -p /home/sarah/workspace
sudo mkdir -p /home/mike/workspace
sudo chown -R sarah:sarah /home/sarah
sudo chown -R mike:mike /home/mike
sudo chmod 700 /home/sarah/workspace
sudo chmod 700 /home/mike/workspace
sudo chage -M 30 sarah
sudo chage -M 30 mike

---

## Task 3: Backup Configuration

### Backup Directories:
- /backups/

### Files Backed Up:
- Apache:
  - /etc/httpd
  - /var/www/html
- Nginx:
  - /etc/nginx
  - /usr/share/nginx/html

### Steps Performed:
- Created required directories
- Created sample files for backup
- Compressed files using tar
- Verified backup integrity
- Created log files
- Scheduled cron jobs for automation

### Commands Used:
sudo mkdir /backups
sudo chmod 777 /backups
sudo tar -czvf /backups/apache_backup_$(date +%F).tar.gz /etc/httpd /var/www/html
sudo tar -czvf /backups/nginx_backup_$(date +%F).tar.gz /etc/nginx /usr/share/nginx/html
tar -tzvf /backups/apache_backup_.tar.gz
tar -tzvf /backups/nginx_backup_.tar.gz
crontab -e
### Cron Job:

0 0 * * 2 tar -czvf /backups/apache_backup_$(date +%F).tar.gz /etc/httpd /var/www/html
0 0 * * 2 tar -czvf /backups/nginx_backup_$(date +%F).tar.gz /etc/nginx /usr/share/nginx/html

---

## Conclusion
Successfully implemented monitoring, secure user management, and automated backups. This project helped understand real-world DevOps practices.