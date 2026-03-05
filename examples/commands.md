OpsLab Commands (SSM Session Manager)
Basic system checks

uname -a
uptime
df -h
free -m

Identify top CPU processes

top -o %CPU
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head

Nginx checks

sudo systemctl status nginx --no-pager
curl -I http://localhost

sudo tail -n 50 /var/log/nginx/access.log
sudo tail -n 50 /var/log/nginx/error.log

(If used) stress-ng test
Note: install may vary by distro and repos

stress-ng --cpu 2 --timeout 120s