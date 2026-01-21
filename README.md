# AWS-Two-Tier-Architecture-with-Terraform-Flask-RDS

## Overview

This project demonstrates a fully functional two-tier architecture on AWS, **entirely implemented and written by me** using Terraform. The infrastructure supports a web application with a secure backend database. Key components include:

* **VPC** with public and private subnets
* **EC2 Instance** hosting a Flask web application
* **RDS MySQL 8.0 Database** in private subnets
* **Security Groups** for controlled network access
* **AWS Secrets Manager** for secure database credential management

All code, modules, and configuration are **originally developed by me**, ensuring secure connectivity and reliable deployment.

---

## Architecture Diagram

![Alt text](https://github.com/Naveen15github/AWS-Two-Tier-Architecture-with-Terraform-Flask-RDS-/blob/f9480ea0076a4897f25eaf2df1e4bd7fc9d41d85/Gemini_Generated_Image_5hmnhq5hmnhq5hmn.png)

## Project Structure

```
day22/
├── main.tf                          # Root module orchestrating all resources
├── variables.tf                     # Root-level variables
├── outputs.tf                       # Outputs of the root module
├── terraform.tfvars.example         # Example configuration values
├── README.md                        # This file 
└── modules/
    ├── vpc/                         # VPC module
    │   ├── main.tf
    │   ├── variables.tf
    │   └── outputs.tf
    ├── security_groups/             # Security groups module
    │   ├── main.tf
    │   ├── variables.tf
    │   └── outputs.tf
    ├── rds/                         # RDS module
    │   ├── main.tf
    │   ├── variables.tf
    │   └── outputs.tf
    └── ec2/                         # EC2 module
        ├── main.tf
        ├── variables.tf
        ├── outputs.tf
        └── templates/
            └── user_data.sh         # EC2 bootstrap script 
```

---

## Prerequisites

* AWS CLI configured with appropriate credentials
* Terraform >= 1.0 installed
* AWS account with permissions to create: VPC, EC2, RDS, Security Groups, and IAM roles

> All setup and configuration steps were implemented and tested by me.

---

## Usage

### 1. Initialize Terraform

```bash
terraform init
```

### 2. Preview Deployment Plan

```bash
terraform plan
```

### 3. Apply Configuration

```bash
terraform apply
```

### 4. Access the Application

Terraform outputs the public URL of the Flask application:

```bash
terraform output application_url
```

Flask app endpoints:

* `/` - Home page
* `/health` - Database health check
* `/db-info` - Database metadata

### 5. Clean Up Resources

```bash
terraform destroy
```

> ⚠️ Important: Destroy the RDS instance after use to avoid unnecessary costs.

---

## Configuration

Create a `terraform.tfvars` file to customize the deployment:

```hcl
project_name = "aws-two-tier"
environment  = "dev"
aws_region   = "us-west-2"

# Database configuration
db_name     = "myappdb"
db_username = "admin"
db_password = "StrongPassword123!"
```

> All configuration values and modules were designed and implemented by me.

---

## Modules

### VPC Module

* Creates the VPC, public and private subnets, route tables, and internet gateway.
* Fully implemented by me.

### Security Groups Module

* **Web Server SG**: Allows HTTP (80) and SSH (22)
* **Database SG**: Allows MySQL (3306) only from the web server
* Entire module written and tested by me.

### RDS Module

* Deploys MySQL 8.0 RDS instance in private subnets
* Connects securely to EC2 using Secrets Manager
* Fully implemented and configured by me.

### EC2 Module

* Ubuntu instance with Flask application
* Bootstrap script installs dependencies and starts Flask app
* Communicates securely with RDS
* Entire implementation authored by me.

---

## Security Considerations

* **No hardcoded credentials**: Secrets Manager used for production-like secure setup.
* **SSH access**: Default is open for testing; restrict in production.
* **Database encryption**: Enabled for production-ready setup.
* **Strong passwords**: Configured for all database users.

> All security practices and implementation decisions were made and applied by me.

---

## Troubleshooting

1. **Flask app not accessible**: Wait 2–3 minutes for EC2 bootstrap to finish.
2. **Database connection errors**: Verify security group rules and RDS status.
3. **RDS provisioning slow**: Can take 5–10 minutes depending on instance type.

> Troubleshooting steps tested and verified by me.

---
## Proof of Work
![Alt text](https://github.com/Naveen15github/AWS-Two-Tier-Architecture-with-Terraform-Flask-RDS-/blob/f9480ea0076a4897f25eaf2df1e4bd7fc9d41d85/Screenshot%20(384).png)
![Alt text](https://github.com/Naveen15github/AWS-Two-Tier-Architecture-with-Terraform-Flask-RDS-/blob/f9480ea0076a4897f25eaf2df1e4bd7fc9d41d85/Screenshot%20(385).png)
![Alt text](https://github.com/Naveen15github/AWS-Two-Tier-Architecture-with-Terraform-Flask-RDS-/blob/f9480ea0076a4897f25eaf2df1e4bd7fc9d41d85/Screenshot%20(386).png)
![Alt text](https://github.com/Naveen15github/AWS-Two-Tier-Architecture-with-Terraform-Flask-RDS-/blob/f9480ea0076a4897f25eaf2df1e4bd7fc9d41d85/Screenshot%20(387).png)
![Alt text](https://github.com/Naveen15github/AWS-Two-Tier-Architecture-with-Terraform-Flask-RDS-/blob/f9480ea0076a4897f25eaf2df1e4bd7fc9d41d85/Screenshot%20(388).png)
![Alt text](https://github.com/Naveen15github/AWS-Two-Tier-Architecture-with-Terraform-Flask-RDS-/blob/f9480ea0076a4897f25eaf2df1e4bd7fc9d41d85/Screenshot%20(389).png)
![Alt text](https://github.com/Naveen15github/AWS-Two-Tier-Architecture-with-Terraform-Flask-RDS-/blob/f9480ea0076a4897f25eaf2df1e4bd7fc9d41d85/Screenshot%20(390).png)


## Outputs

| Output Name             | Description                 |
| ----------------------- | --------------------------- |
| `vpc_id`                | ID of the created VPC       |
| `web_server_public_ip`  | Public IP of EC2 instance   |
| `web_server_public_dns` | Public DNS of EC2 instance  |
| `application_url`       | URL to access the Flask app |
| `rds_endpoint`          | RDS instance endpoint       |
| `rds_port`              | RDS instance port           |
| `database_name`         | Name of the MySQL database  |

> All outputs are generated from resources **implemented and configured by me**.


