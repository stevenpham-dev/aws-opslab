# Teardown — AWS OpsLab

Purpose: remove AWS resources to avoid ongoing costs.

## Terminate EC2
- **EC2 → Instances**
  - Terminate: `AWS-OpsLab-EC2`

## Delete CloudWatch resources
- **CloudWatch → Alarms**
  - Delete: `OpsLab-CPU-High`
- **CloudWatch → Dashboards**
  - Delete: `AWS-OpsLab-Dashboard`
- **CloudWatch → Log groups** (optional cleanup)
  - Delete:
    - `AWS-OpsLab-nginx-access`
    - `AWS-OpsLab-nginx-error`

## Delete SNS
- **SNS → Topics**
  - Delete: `AWS-OpsLab-Alerts`

## Delete IAM role (if created specifically for OpsLab)
- **IAM → Roles**
  - Delete: `AWS-OpsLab-EC2-SSMRole`