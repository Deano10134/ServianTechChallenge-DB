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

Github will be used to store and host the repos.


# Architecture
The AWS environment will be set up with the following to host the application

Amazon RDS instance to host the Database accross a Multiple AZ 
EC2 instance to host the application that will be connect to a Auto Scaling Group to ensure that it is high available to scable to meet peek demands
A Elastic Load balancer will be attached to the VPC 
