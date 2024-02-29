# AWS-WordPress-website Project

![image](https://github.com/ImaniChristianne/AWS-WordPress-website/assets/111906526/155fc27a-c947-4190-970c-074f24c31db7)


## Project Description 

Welcome to my AWS WordPress website project! I built a robust and scalable WordPress website hosted on AWS following a comprehensive tutorial by Azeez Salu on aosnote.com.

### Key Features:

AWS Infrastructure --> Leveraging AWS services such as EC2, RDS, S3, and CloudFront to create a reliable and high-performance hosting environment for WordPress.

WordPress Setup --> Setting up WordPress on AWS instances and configuring it for optimal performance and security.

Scalability --> Implementing auto-scaling features and load balancing to handle varying levels of traffic efficiently.

Security --> Employing best practices for securing the WordPress installation and AWS infrastructure against common threats.

Continuous Deployment --> Integrating with CI/CD pipelines for automated deployment and updates.

## Project Steps 

### Create VPC 

- [Create a Virtual Private Cloud (VPC)](https://docs.aws.amazon.com/vpc/latest/userguide/create-vpc.html )
- Configure DNS hostnames
- Attach an Internet Gateway to the VPC for external connectivity
- Establish two public subnets across two Availability Zones, ensuring that they are configured to auto-assign public IPv4 addresses
- Create a public route table and link it to the Internet Gateway, with subnet associations established to connect it with the public subnets
- Create four private subnets and verify their association with the main route table to ensure proper network routing within the VPC.

### Create Nat Gateways

To enable outbound internet access for resources in private subnets across multiple Availability Zones, we create NAT Gateways and configure private route tables accordingly.

- [Create a NAT Gateway in the public subnet of Availability Zone 1 (AZ1)](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html)
- Set up a private route table specific to AZ1, adding routes that point to the NAT Gateway
- Associate this route table with the private subnets in AZ1 to establish connectivity
- Repeat the process for Availability Zone 2 (AZ2)

### Create the Security Groups

- Create an ALB Security Group for Application Load Balancer (Port = 80 and 443)
- Create an SSH Security Group (Port = 22)
- Create a Webserver Security Group (Port = 80 and 443, Source = ALB Security Group. Port = 22, Source = SSH Security Group)
- Create a Database Security Group (Port = 3306, Source = Webserver Security Group)
- Createan an EFS Security Group for EFS File System

### Create the RDS Instance

- Create DB subnet group
- Create the database instance using RDS

### Create the Elastic File System (EFS)

- [Create the EFS file system](https://docs.aws.amazon.com/efs/latest/ug/gs-step-two-create-efs-resources.html)
- Configure Mount targets within two Private Data Subnets during the creation process. These Mount targets serve as connection points for the webservers to access the EFS

### Install WordPress
- Launch an EC2 instance on Public Subnet AZ1
- Connect to your instance via the AWS 'Conneect' to instance option
- On terminal, [run several commands to install WordPress step by step](https://github.com/azeezsalu/wordpress-project-commands/blob/abaada4048b599a9b8d71f867f447a2304d9e385/7.%20Install%20WordPress.txt)
- Configure the wp-config.php file using the information of the database created
- Restart the webserver
- Enter the IPv4 address of EC2
- Register the WordPress account
- Login on on this account

### Create an Application Load Balancer

- Launch a EC2 instance WebServer AZ1 on Private App Subnet AZ1. [Insert user data in the user data field in AWS](https://github.com/azeezsalu/wordpress-project-commands/blob/abaada4048b599a9b8d71f867f447a2304d9e385/8.%20Create%20an%20Application%20Load%20Balancer.txt)
- Launch a EC2 instance WebServer AZ2 on Private App Subnet AZ2
- Create target group Dev-TG
- Register your target with Webserver AZ1 and Webserver AZ2
- Create load balancer Dev-ALB
- Map it to Public Subnet AZ1 and Public Subnet AZ2
- Copy the DNS name of the Application Load Balancer
- Login in the WordPress Dashboard
- Use the copied DNS name to change the WordPress Address and Site Address.
- Remove the '/' at the end on both fields
- Terminate the setup server

### Register a New Domain Name in Route 53

- Access the Route 53 Dashboard in the AWS console
- Input the desired domain name
- Verify its availability, and then proceed to purchase the selected domain name.

### Create a Record Set in Route 53

- On the Route 53 Dashboard, within the hosted zones section, generate the record.
- Log in to WordPress utilizing the newly established record name.
- Modify the URL in WordPress accordingly, remembering to remove the '/' at tthe end. 

### Register for an SSL Certificate in AWS Certificate Manager

- Create the public certificate in AWS Certificate Manager
- Create records in Route 53 for the certificate
  
### SSH into Instance in the Private Subnet

- Launch an EC2 instance Bastion Host in the public subnet AZ1
- Connect to the instance in AWS terminal
- Proceed to ssh into the private subnet instances

### Create an HTTPS Listener for the Application Load Balancer

- Locate your existing load balancer and configure a new listener.
- Adjust the port 80 listener to redirect HTTP traffic to HTTPS.
- Access the webserver in AZ1 via ssh
- Modify the wp-config.php file
- Append "/wp-admin" to the domain name to access the dashboard and update the URL.

### [Create an Auto Scaling Group](https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-asg-launch-template.html)

### Install WordPress Theme and Template

- Under the Appearance section of the WordPress website, click themes.
- Pick a theme and apply it

## Credits

The tutorials provided by Azeez Salu on aosnote.com were instrumental in the development of this project.

Instructor: Azeez Salu
Tutorial Source: aosnote.com
GitHub Repository: Azeez Salu's Aosnote Projects
