# Deploy-a-High-Availability-Web-App-Using-CloudFormation

# Table of Contents
* Overview
* Web Application
* Infrastructure Requirements
* * Server Specifications
* * Security Groups and Roles
* Infrastructure Deployment
* * Create Infrastructure
* * Verify Deployment
* * Update Infrastructure
* * Delete Infrastructure
* Deployed Infrastructure Output
* Web App Output
* Project Files
* References

## Overview

This project is second of the Udacity Cloud DevOps Engineer Nanodegree.

The objective of the project is to deploy a high availability web application using AWS CloudFormation.
The website will be accessed through a website-endpoint.

## Web Application

The web application includes an html file displaying the message "My Udacity Udagram Demo Web Server App is Up and Running!"

This project implements network and server infrastructures as a code.

# Infrastructure Requirements

## Server Specifications

The diagram below shows the overview of the infrastructure needed to be deployed:

![Infrastructure-diagram](https://github.com/eaamankwah/deploy-a-high-availability-webapp/blob/main/screenshots/infra-diagram.png)

* Created a Launch Configuration for the application servers in order to deploy four servers, two located in each of your private subnets. The launch configuration will be used by an auto-scaling group.
* The following resources were used:
** two vCPUs  
** 4GB of RAM. 
** Ubuntu 18 Operating System and 
** At least 10GB of disk space. 

## Security Groups and Roles
* Created and AWS root role and role policy to that allowed downloading the application archive from an S3 Bucket.

* Web application communicated on a default HTTP Port: 80.
* Servers had inbound port open to allow Load Balancer and Load Balancer Health Check. 
* Servers had outbound port unrestricted internet access to be able to download and update software.
* Load balancer allowed all public traffic (0.0.0.0/0) on port 80 inbound, which is the default HTTP port. Outbound was only used on port 80 to reach the internal servers.
* Application was deployed into private subnets with a Load Balancer located in a public subnet.
* One of the output exports of the CloudFormation script was the public URL of the LoadBalancer. 
* Hhttp:// was added in front of the load balancer DNS Name in the output, for convenience.

# Infrastructure Deployment

## Create Infrastructure

The following stack commands were run to create network and servers' infrastructure:

1. `./create.sh network network.yml network-parameters.json`                                    

2. `./create.sh servers servers.yml servers-parameters.json`  

## Verify Deployment

The web application was verified to be running by accessing the value under the output of the servers' cloud formation stack. 

## Update Infrastructure

The already existing infrastructure stack were updated by running the following stack commands:

1. `./update.sh network network.yml network-parameters.json`                                    

2. `./update.sh servers servers.yml servers-parameters.json`  

## Delete Infrastructure

The deployed infrastructure was deleted by running the following stack commands:

1. `./delete.sh servers`  

2. `./delete.sh network` 

# Deployed Infrastructure Output

The following screenshots indicate indicates the successful deployment of network and server infrastructure:

![Network-output](https://github.com/eaamankwah/deploy-a-high-availability-webapp/blob/main/screenshots/network-output.png) 

![Network-events](https://github.com/eaamankwah/deploy-a-high-availability-webapp/blob/main/screenshots/network-events.png) 

![Deployed-servers](https://github.com/eaamankwah/deploy-a-high-availability-webapp/blob/main/screenshots/server-info.png) 

![Server-events](https://github.com/eaamankwah/deploy-a-high-availability-webapp/blob/main/screenshots/server-events.png) 

![Server-resources](https://github.com/eaamankwah/deploy-a-high-availability-webapp/blob/main/screenshots/server-resources.png) 

# Web App Output

Below is the link to my web app showing that everything works

http://serve-WebAp-1S5DR3Y22NVIO-2004577092.us-west-2.elb.amazonaws.com

The screenshots below indicate web application output and hyperlink:

![Webapp-output](https://github.com/eaamankwah/deploy-a-high-availability-webapp/blob/main/screenshots/webapp-output.png) 

![Webapp-hyperlink](https://github.com/eaamankwah/deploy-a-high-availability-webapp/blob/main/screenshots/webapp-hyperlink.png) 

# Project Files

1. README.md - provides discussion on your project
2. Infrastructure Diagram - displays visual aid to understand the CloudFormation script that was eventually turned into infrastructure as a code.
3. Network.yml - template containing network infrastructure
4. Network-parameters.json - json file containing parameters for the network
5. Servers.yml - template containing servers' infrastructure
6. Servers-parameters.json - json file containing parameters for the servers
7. create.sh - file containing stack commands to create network and server infrastructure.
8. update.sh - file containing stack commands to update server infrastructure.
9. delete.sh - file containing stack commands to delete network and server infrastructure.
10. udacity.zip - compressed file containing the web application message that was uploaded to s3
11. Screenshot images - displays major steps from beginning to the end of the project.

# References

* [AWS CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)

* [Udacity Q & A Platform](https://knowledge.udacity.com/?nanodegree=nd9991&page=1&project=613&rubric=2556)
