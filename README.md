# Project2-Apache

In this project, an Apache hosted website is deployed in the cloud using the Amazon AWS. The network infrastructure, (application load balancer, private subnets, public subnets, elastic IPs, NAT gateways, VPC, auto scaling, and availability zones), is provisioned using CloudFormation (Infrastructure-as-code). There are two branches in this repo. The master branch is developed using a Windows machine while the second branch is developed using a Linux/ubuntu machine. Moreover, in the second branch, we show how to provision a bastion/proxy machine in the public subnet to facilitate debugging the web servers that are deployed in the private subnets.

## Usage

First, you need to configure your machine to have access to an IAM user in AWS cloud. Then, we can provision the whole infrastructure by running the following bash command:

<code>aws cloudformation create-stack --stack-name prod --template-body file://project-template.yaml  --parameters file://project-parameters.json --capabilities "CAPABILITY_IAM" "CAPABILITY_NAMED_IAM" --region=us-west-2</code>

where `prod` is the name of the stack, `project-template.yaml` is the network infrastructure to be provisioned, and `project-parameters.json` is the parameters passed to the project template, such as the CIDRs of the private subnets.
