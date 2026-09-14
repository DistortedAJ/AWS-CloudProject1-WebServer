
# AWS VPC Web Server

## Project Overview

This project demonstrates the deployment of a basic web server in Amazon Web Services (AWS). I created a custom Virtual Private Cloud (VPC), configured public and private subnets, established internet routing, configured security group firewall rules, and deployed a Linux EC2 instance running Nginx.

## Architecture

```text
                    Internet
                       |
                Internet Gateway
                       |
                  Public Route
                    Table
                       |
                 Public Subnet
                  10.0.1.0/24
                       |
                 EC2 Web Server
                    Linux
                    Nginx
                       |
                  index.html

                 Private Subnet
                  10.0.2.0/24
```

## Technologies Used

* Amazon Web Services (AWS)
* Amazon VPC
* Amazon EC2
* Linux
* Nginx
* IPv4/CIDR
* Route Tables
* Internet Gateway
* Security Groups
* SSH / EC2 Instance Connect
* GitHub

## What I Built

### 1. VPC

Created a custom VPC:

```text
VPC: Resume-Project-VPC
CIDR: 10.0.0.0/16
```

The VPC provides an isolated network environment for the AWS resources used in the project.

### 2. Subnets

Created two subnets:

```text
Public Subnet
10.0.1.0/24

Private Subnet
10.0.2.0/24
```

The public subnet is designed for resources that need internet connectivity, while the private subnet provides a separate network segment for resources that should not be directly exposed to the internet.

### 3. Internet Gateway and Routing

Created and attached an Internet Gateway to the VPC.

Configured the public route table with:

```text
Destination: 0.0.0.0/0
Target: Internet Gateway
```

This allows resources in the public subnet to communicate with the internet when their network configuration and security rules permit it.

### 4. Security Group

Created a security group for the web server.

Configured inbound traffic for:

```text
SSH  - TCP 22
HTTP - TCP 80
```

The security group acts as a virtual firewall controlling network traffic to the EC2 instance.

### 5. EC2 Web Server

Deployed a Linux EC2 instance inside the public subnet.

Connected to the instance using EC2 Instance Connect and configured the Linux server.

### 6. Nginx

Installed and started Nginx:

```bash
sudo yum install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

Nginx was used to serve the project's HTML webpage.

### 7. Website

Created:

```text
/usr/share/nginx/html/index.html
```

The webpage confirms that the server is successfully running and accessible through the internet.

## What I Learned

Through this project, I gained hands-on experience with:

* Cloud networking
* VPC architecture
* IPv4 CIDR addressing
* Network segmentation
* Route tables
* Internet gateways
* AWS security groups
* Linux server administration
* Nginx web servers
* SSH/EC2 Instance Connect
* Basic cloud troubleshooting

## Challenges

One of the main challenges was understanding how the different AWS networking components work together. I learned that creating an EC2 instance alone does not make it accessible from the internet. The VPC, subnet, route table, Internet Gateway, public IP, and security group all play a role in establishing connectivity.

## Result

Successfully deployed a publicly accessible Linux web server in AWS and hosted a custom HTML webpage through Nginx.

## Future Improvements

Potential improvements include:

* Deploying the web server in an Auto Scaling Group
* Adding an Application Load Balancer
* Adding HTTPS with SSL/TLS
* Deploying a database in the private subnet
* Using Terraform to automate the infrastructure
* Adding CloudWatch monitoring

