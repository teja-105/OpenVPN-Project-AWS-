# OpenVPN-Project (AWS)

Step 1: VPC Setup

    Created a Virtual Private Cloud (VPC):
        CIDR Block: 10.0.0.0/16
        This VPC serves as the network for hosting both the OpenVPN server and private server.

    Configured Subnets:
        Public Subnet: CIDR Block 10.0.1.0/24 (for hosting the OpenVPN server).
        Private Subnet: CIDR Block 10.0.2.0/24 (for hosting the private server, isolated from direct internet access).

    Attached an Internet Gateway (IGW):
        The IGW was attached to the VPC to enable internet connectivity for the public subnet.

    Configured Route Tables:
        Public Route Table:
            Added a route for all internet traffic (0.0.0.0/0) directed to the IGW.
            Associated this route table with the public subnet.
        Private Route Table:
            No route to 0.0.0.0/0, ensuring that the private subnet could not directly access the internet.
            Configured this route table to allow local traffic only.
            Named this route table PublicSubnetRoutetable.

Step 2: EC2 Instance Setup

    Launched a Private Server:
        Instance launched in the Private Subnet.
        No public IP assigned to ensure it remains isolated.
        Named this instance "Private Server".

    Launched an OpenVPN Server:
        Instance launched in the Public Subnet using the OpenVPN Access Server AMI from the AWS Marketplace.
        Named this instance "OpenVPN Server".

Step 3: OpenVPN Configuration

    Configured the OpenVPN Server:
        Connected to the OpenVPN Server from the AWS management console.
        Completed initial setup for the admin interface, including user authentication and network settings.

    Set Up the Client Application:
        Installed the OpenVPN client application on my personal laptop.
        The application included a toggle button for switching the VPN connection on and off.

    Testing Connectivity:
        Initially attempted SSH to the private server from my laptop, which failed since it lacked direct access to the private subnet.
        Connected to the OpenVPN server using the client application, effectively making my laptop part of the VPC.
        Retried SSH to the private server and successfully connected.

Step 4: Security Configuration

    Private Server Security Group:
        Allowed inbound traffic on port 22 (SSH) only from the OpenVPN server.

    Public Server Security Group:
        Configured to allow necessary inbound and outbound traffic for OpenVPN functionality.

Outcome:
The project successfully established a secure and scalable VPN solution in AWS. By leveraging OpenVPN, I ensured secure remote access to resources in the private subnet while maintaining strict network isolation. This design provides a foundation for secure and efficient cloud networking.
