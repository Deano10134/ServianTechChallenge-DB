# Servian-Tech-challenge_DB
This repository will show my solution to deploy the application for the Servian Tech challenge to the AWS Cloud environment.

# Prerequisites

To deploy this database application to AWS the following needs to be set up on your system.

1. Set up Terraform

To set# Servian-Tech-challenge_DB
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
2. Install the AWS CLI
To Install the AWS CLI see AWS documentation https://aws.amazon.com/cli/

3. Set up your IDE of choice for this I'm using VS Code on Windows. VS code can be installed on all operating systems for details see 
https://code.visualstudio.com/

The IDE is where the code for the application will be set up.

# Architecture
The AWS environment will be set up with the following to host the application

Amazon RDS instance to host the Database across a Multiple AZ 
EC2 instance to host the application that will be connected to an Auto Scaling Group to ensure that it is highly available to scalable to meet peak demands
An Elastic Load balancer will be attached to the VPC 
An S3 bucket will be hosting the files of the application.

# Network
In the AWS environment, there will be one VPC with 2 subnets one that is Public and one that is private. The Private and Public VPCs will be set across two Availablity Zones. The RDS instance will be set up in the two AZs and will be public so it is publically accessible. 
# Security

Security considerations that will need to be considered include ensuring that the data is encrypted at rest and that the S3 bucket is not accessible by default and that the right security rules in the VPC are implemented.
