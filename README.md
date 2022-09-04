# Servian-Tech-challenge_DB
This repository will show my solution to deploy the application for the Servian Tech challenge to the AWS Cloud environment.

# Prerequisites

To deploy this database application to AWS the following needs to be setup on your system.

1. Set up Terraform

To setup Terraform on Windows visit Terraform's website https://www.terraform.io/downloads

2. Install the AWS CLI

To Install the AWS CLI see AWS documentation https://aws.amazon.com/cli/

3. Set up your IDE of choice for this I'm using VS Code on Windows. VS code can be installed on all operating systems for details see 
https://code.visualstudio.com/

The IDE is where the code for the application will be set up.

4. Github

GitHub will be used to store and host the repos. It also is where the code for the application is updated. 

5. Terraform

To set up Terraform on Windows visit Terraform's website https://www.terraform.io/downloads and follow the instructions. 

Terraform will be used to deploy the application to AWS. It can be set up to use AWS account credentials, using the secret access key for your AWS user.
# Architecture
The AWS environment will be set up with the following to host the application

Amazon Aurora DB instance to host the Database across a Multiple AZ 
EC2 instance to host the application that will be connected to an Auto Scaling Group to ensure that it is highly available to scalable to meet peak demands. The EC2 Auto scaling group will be set up between two availability zones. 
An Elastic Load balancer will be attached to the VPC and help distribute the workloads of the application. 
An S3 bucket will be used to host the files of the application. It will be stored in a folder available on an S3 bucket.
 
 
# Network
In the AWS environment, there will be one VPC with 2 subnets one that is Public and one that is private. The Private and Public VPCs will be set across two Availablity Zones. The Amazon Auroa instance will be set up in the two AZs and will be public so it is publically accessible. 

# Security

Security considerations that will need to be considered include ensuring that the data is encrypted at rest and that the S3 bucket is not accessible by default and that the right security rules in the VPC are implemented. 

The VPC would be set up with Twos subnets.

Public and Private.
Each subnet would have the appropiate Security group rules applied them. Below is an example of one such rule in a public subnet.

The rules in the public subnet would be the following:

- The outbound security group rules will allow HTTP traffic fron any IP address. (accept the default SG rules)

- The Inbound rules will allows SSH from the host's IP address for example 110.22.23.** HTTP and HTTPS will be also be enabled in the inbound Security group rules.

#Secret Management

- In AWS to manage secrets between accounts it best practice to rotate the secrets. A services that lets you create secrets is called AWS KMS and the keys can be stored in AWS secrets manager. 

In this solutions I would uses secrets manager to store the databases credientals in AWS. 

#CI/CD

In AWS I would use CodeCommit to deploy the application through a CI/CD Pipeline. This would update any changes to the app.


