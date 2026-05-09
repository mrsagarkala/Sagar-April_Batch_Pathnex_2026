
Complete the following:

- Create EC2 (choose: c5.xlarge / r5.2xlarge / r6i.4xlarge / c6i.8xlarge / c6a.12xlarge)
- Security group
- Key pair
- EBS volume
- Output IP

- Install nginx
- Deploy "Welcome to Pathnex" HTML page
- Start & enable service

- Create Deployment with PVC
- Expose via NodePort

- Print 5 system checks:
  - CPU
  - Memory
  - Disk
  - IP
  - Top process


Complete the following:

- Create EC2 (choose: c5.xlarge / r5.2xlarge / r6i.4xlarge / c6i.8xlarge / c6a.12xlarge)
- Security group
- Key pair
- EBS volume
- Output IP

- Install nginx
- Deploy "Welcome to Pathnex" HTML page
- Start & enable service

- Create Deployment with PVC
- Expose via NodePort

- Print 5 system checks:
  - CPU
  - Memory
  - Disk
  - IP
  - Top process

You will learn to **combine all tasks into a realistic Jenkins Pipeline** with proper stages and tags.

- Create **Declarative Pipeline** with stages:
- Infrastructure – apply Terraform to create EC2, Security Group, Key Pair, and EBS volume
- App Deployment – run Ansible playbooks and deploy Kubernetes resources
- Monitoring Checks – execute shell scripts to check:
- CPU
- Memory
- Disk
- IP
- Top process

- Use environment variables for all stages:
- INSTITUTE_NAME = "Pathnex"
- TEAM = "DevOps"
- ENV = "prod"
- PROJECT = "Pathnex-Training"

You will learn to **combine all tasks in a realistic GitLab CI pipeline**.

- Create `.gitlab-ci.yml` with stages:
- infrastructure – Terraform apply for EC2, SG, Key Pair, EBS
- app_deployment – Ansible and Kubernetes deployment
- monitoring_checks – Shell scripts to check:
- CPU
- Memory
- Disk
- IP
- Top process

- Define variables:
- INSTITUTE_NAME = "Pathnex"
- TEAM = "DevOps"
- ENV = "prod"
- PROJECT = "Pathnex-Training"