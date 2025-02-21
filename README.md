# AWS CloudFormation VPC with Web and Private Servers

## Overview
This CloudFormation template provisions an AWS Virtual Private Cloud (VPC) with both public and private subnets, deploys an Apache web server in the public subnet, and launches a private EC2 instance with AWS Systems Manager (SSM) access.

## Resources Created
- **VPC** with CIDR block `10.0.0.0/16`
- **Public Subnet** (CIDR: `10.0.1.0/24`)
- **Private Subnet** (CIDR: `10.0.3.0/24`)
- **Internet Gateway** for internet access to public resources
- **NAT Gateway** for private subnet internet access
- **Route Tables** for public and private subnets
- **IAM Role & Instance Profile** for EC2 instances with SSM access
- **Security Group** allowing HTTP (80) and SSH (22) access
- **Public Web Server** running Apache
- **Private Server** accessible via SSM

## Deployment Steps
1. **Launch CloudFormation Stack:**
   - Use AWS CloudFormation and provide the template.
   - Ensure the necessary parameters are configured.

2. **Access the Web Server:**
   - Retrieve the public IP of the web server from the AWS console.
   - Open a browser and navigate to `http://<Public-IP>` to see the Apache welcome page.

3. **Connect to the Private Server via SSM:**
   - Open AWS Systems Manager Session Manager.
   - Select the private instance and start a session.

4. **Pinging the Servers:**
   - To ping the Web Server from your local machine:
     ```sh
     ping <Public-IP>
     ```
   - To ping the Private Server from within the Web Server:
     ```sh
     ping <PRIVATE-IP>
     ```

## Notes
- The private instance has no direct internet access and must use SSM for management.
- The web server hosts a simple page displaying `Hello, my name is Moses Winbood Ayandau`.

## Cleanup
To delete all resources, remove the CloudFormation stack from the AWS console.

---
This template provides a robust AWS environment with secure access and public-private networking principles.

