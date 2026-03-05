Teardown — AWS OpsLab

Purpose: remove AWS resources to avoid ongoing costs.

EC2

Terminate instance: AWS-OpsLab-EC2

Delete associated security group(s) if created for this project

Delete key pair if created (optional)

IAM

Remove instance profile / role if created specifically:

Role: AWS-OpsLab-EC2-SSMRole

CloudWatch

Delete alarms:

OpsLab-CPU-High

Delete dashboard:

AWS-OpsLab-Dashboard

Delete log groups (optional cleanup):

AWS-OpsLab-nginx-access

AWS-OpsLab-nginx-error

SNS

Delete SNS topic:

AWS-OpsLab-Alerts

Final sanity check

EC2: no running instances for OpsLab

CloudWatch: alarms removed

CloudWatch Logs: log groups removed (optional)

SNS: topic removed