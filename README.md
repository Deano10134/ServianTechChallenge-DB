# ServianTechChallenge-DB
This repository will show my solution to deploy the application for the Servian Tech challenge to the AWS Cloud environment.

# Prerequisites

To deploy this database application to AWS the following needs to be setup on your system.

1. Set up Terraform

Terraform is an Infrastructure as code deployment solution that allows you to deploy applications to your Cloud provider of choice without having to manually manage your infrastructure. It is open source and compatible with any operating system. In this example I have set it up on Windows and used AWS as my cloud provider of choice.

To setup Terraform on Windows visit Terraforms website https://www.terraform.io/downloads.
Terraform will be used to deploy the application to AWS. It can be set up to use AWS account credentials, using the secret access key for your AWS user.

2. Install the AWS CLI

To Install the AWS CLI, see AWS documentation https://aws.amazon.com/cli/

3. Set up your IDE of choice for this I'm using VS Code on Windows. VS code can be installed on all operating systems for details see 
https://code.visualstudio.com/

The IDE is where the code for the application will be set up.

4. Github

GitHub will be used to store and host the repos. It also is where the code for the application is updated. 

5. Docker 

Install Docker for desktop to setup the application and get the latest code. 


# Architecture
The AWS environment will be set up with the following to host the application:

- Amazon Aurora DB with PostgreSQL instance to host the Database across a Multiple AZ 
- EC2 instance to host the application that will be connected to an Auto Scaling Group to ensure that it is highly available to scalable to meet peak demands. The EC2 Auto scaling group will be set up between two availability zones. 
- An Elastic Load balancer will be attached to the VPC and help distribute the workloads of the application. 
- An S3 bucket will be used to host the files of the application. It will be stored in a folder available on an S3 bucket.

 ![Servian-challenge](https://user-images.githubusercontent.com/13935623/188301970-d8047494-0dfa-4655-83d8-67493a6f7f56.jpg)
 
The diagram above shows a basic architecture of the AWS environment. It excludes Security Group rules, CodeCommit and Secrets Manager that would be added if I had more time to deploy the application to AWS. 
 
# Network
In the AWS environment, there will be one VPC with 2 subnets one that is Public and one that is Private. The Private and Public VPCs will be set across two Availability Zones. The Amazon Aurora instance will be set up in the two AZs and will be placed in the private subnet. While the EC2 instances that run the application would be placed in the public subnet and connected to a Elastic Load balancer. The Amazon Aurora instance would be connected to the EC2 instance.

# Security

Security considerations that will need to be considered include ensuring that the data is encrypted at rest and that the S3 bucket is not accessible by default and that the right security rules in the VPC are implemented. 

The VPC would be set up with Twos subnets.

Public and Private.
Each subnet would have the appropriate Security group rules applied to them. Below is an example of one such rule in a public subnet.

The rules in the public subnet would be the following:

- The outbound security group rules will allow traffic from any IP address. (Accept the default SG rules)

- The Inbound rules will allow SSH from the host's IP address for example 110.22.23.** HTTP and HTTPS will also be enabled in the inbound Security group rules.

The subnet that the Database is deployed in would have to allow port


# Secret Management

- In AWS to manage secrets between accounts you can used a service called AWS KMS and the keys can be stored in AWS secrets manager. 

In this solution I would uses secrets manager to store the databases credentials in AWS. 

# CI/CD

In AWS I would use CodeCommit to deploy the application through a CI/CD Pipeline. This would update any changes to the app.

Also, if given more time I would use CloudFormation to deploy the templates for the Auto Scaling group and use CloudWatch to monitor the Application for performance.

# Health Checks

To verify that the applications work once it would be deployed it would be tested that the application is accessible by the EC2 instance IP address endpoint.
