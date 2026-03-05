RUNBOOK: High CPU Alarm (EC2) — OpsLab

Trigger

CloudWatch Alarm: OpsLab-CPU-High

Condition: CPUUtilization > 50% for 1 minute

Notification: SNS email

Immediate Checks

Confirm alarm state and timeline in CloudWatch (graph, period = 1 min).

Verify instance health checks (EC2 status checks 2/2).

Confirm service health:

Open public URL in browser OR curl from instance.

Access Method (No SSH)

Use AWS Systems Manager Session Manager to connect.

Commands

Identify top CPU processes:

top -o %CPU

ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu | head

Check web service:

sudo systemctl status nginx --no-pager

curl -I http://localhost

Check logs (local):

sudo tail -n 50 /var/log/nginx/access.log

sudo tail -n 50 /var/log/nginx/error.log

Check logs (CloudWatch):

View log group AWS-OpsLab-nginx-access and confirm recent entries.

Mitigation

If a runaway process is found: stop/restart service or kill offending PID (only if safe).

If nginx is down: sudo systemctl restart nginx

If resources are insufficient: consider scaling up instance type or adding Auto Scaling.

Resolution Verification

CPU returns to baseline.

Alarm transitions to OK.

Website responds 200 OK.

Logs continue updating in CloudWatch.