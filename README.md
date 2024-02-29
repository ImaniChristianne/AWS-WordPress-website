# AWS-WordPress-website Project

![image](https://github.com/ImaniChristianne/AWS-WordPress-website/assets/111906526/155fc27a-c947-4190-970c-074f24c31db7)


## Project Description 

Welcome to my AWS WordPress website project! This project is a culmination of following a comprehensive tutorial by Azeez Salu on aosnote.com, where I learned how to build a robust and scalable WordPress website hosted on Amazon Web Services (AWS).

### Key Features:

AWS Infrastructure: Leveraging AWS services such as EC2, RDS, S3, and CloudFront to create a reliable and high-performance hosting environment for WordPress.

WordPress Setup: Setting up WordPress on AWS instances and configuring it for optimal performance and security.

Scalability: Implementing auto-scaling features and load balancing to handle varying levels of traffic efficiently.

Security: Employing best practices for securing the WordPress installation and AWS infrastructure against common threats.

Continuous Deployment: Integrating with CI/CD pipelines for automated deployment and updates.

## Project Steps 

### Create VPC 

- [Create a Virtual Private Cloud (VPC)](https://docs.aws.amazon.com/vpc/latest/userguide/create-vpc.html )
- Configure DNS hostnames
- Attach an Internet Gateway to the VPC for external connectivity
- Establish two public subnets across two Availability Zones, ensuring that they are configured to auto-assign public IPv4 addresses
- Create a public route table and link it to the Internet Gateway, with subnet associations established to connect it with the public subnets
- Create four private subnets and verify their association with the main route table to ensure proper network routing within the VPC.

### Create Nat Gateways
### Create the Security Groups
### Create the RDS Instance
### Create the Elastic File System (EFS)
### Install WordPress
### Create an Application Load Balancer
### Register a New Domain Name in Route 53
### Create a Record Set in Route 53
### Register for an SSL Certificate in AWS Certificate Manager
### SSH into Instance in the Private Subnet
### Create an HTTPS Listener for the Application Load Balancer
### Create an Auto Scaling Group
### Install WordPress Theme and Template

## Credits

The tutorials provided by Azeez Salu on aosnote.com were instrumental in the development of this project.

Instructor: Azeez Salu
Tutorial Source: aosnote.com
GitHub Repository: Azeez Salu's Aosnote Projects
