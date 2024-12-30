# OpenVPN-Project (AWS)

## Description
This project demonstrates a secure and scalable VPN solution using OpenVPN in an AWS environment. A custom VPC was designed with separate public and private subnets to ensure controlled traffic flow and high-security standards. The following is the detailed step-by-step process:

## Step 1: VPC Setup
### 1. Created a Virtual Private Cloud (VPC):
- CIDR Block: `10.0.0.0/16`  
- This VPC serves as the network for hosting both the OpenVPN server and private server.

### 2. Configured Subnets:
- Public Subnet: CIDR Block `10.0.1.0/24` (for hosting the OpenVPN server).  
- Private Subnet: CIDR Block `10.0.2.0/24` (for hosting the private server, isolated from direct internet access).

### 3. Attached an Internet Gateway (IGW):
- The IGW was attached to the VPC to enable internet connectivity for the public subnet.

### 4.Configured Route Tables:
  #### Public Route Table:
- Added a route for all internet traffic (0.0.0.0/0) directed to the IGW.  
-  Associated this route table with the public subnet.  
  #### Private Route Table:
- No route to `0.0.0.0/0`, ensuring that the private subnet could not directly access the internet.  
- Configured this route table to allow local traffic only.
- Named this route table PublicSubnetRoutetable.

  ## Step 2: EC2 Instance Setup

  ### 1. Launched a Private Server:
  - Instance launched in the Private Subnet.  
  - No public IP assigned to ensure it remains isolated.  
  - Named this instance `Private Server`.

  ### 2. Launched an OpenVPN Server:
  - Instance launched in the Public Subnet using the OpenVPN Access Server AMI from the AWS Marketplace.  
  - Named this instance `OpenVPN Server`.
