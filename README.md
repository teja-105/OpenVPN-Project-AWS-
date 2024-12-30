# OpenVPN-Project (AWS)

## Description
This project demonstrates a secure and scalable VPN solution using OpenVPN in an AWS environment. A custom VPC was designed with separate public and private subnets to ensure controlled traffic flow and high-security standards. The following is the detailed step-by-step process:

## Step 1: VPC Setup
### 1. Created a Virtual Private Cloud (VPC):
> CIDR Block: 10.0.0.0/16
> This VPC serves as the network for hosting both the OpenVPN server and private server.
### 2. Configured Subnets:
Public Subnet: CIDR Block 10.0.1.0/24 (for hosting the OpenVPN server).
Private Subnet: CIDR Block 10.0.2.0/24 (for hosting the private server, isolated from direct internet access).
