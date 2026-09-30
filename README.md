# AWS Cloud Deployment & Automation Project

## Overview

A practical cloud deployment project where I containerized a static web application and developed the AWS infrastructure and deployment workflow around it.

## Architecture

Internet
-> Application Load Balancer
-> Target Group
-> EC2 instances running my Docker/Nginx

GitHub
-> GitHub Actions
-> Amazon ECR
-> EC2 deployment

With supporting services such as VPC, IAM, S3, CloudWatch

## Technologies

AWS
Linux
Docker
Nginx
Amazon EC2
Amazon VPC
Application Load Balancer
Auto Scaling
Amazon ECR
Amazon S3
IAM
GitHub Actions
CloudWatch

## What I did

Containerized a static website with Docker and Nginx.
Deployed it to EC2 behind an Application Load Balancer
Configured Auto Scaling, target health checks as well as CloudWatch monitoring.

## CI/CD

1. Code is pushed to GitHub
2. The GitHub Actions workflow is triggered
3. It builds and validates the Docker image
4. The image is pushed to ECR
5. The deployment step is triggered to update the running application
6. The application is verified

## Testing

Verified that my local Docker deployment worked
Verified ALB health checks
Tested one unhealthy backend target and confirmed traffic rerouting
Tested ASG instance replacement after a manual termination
Tested the whole GitHub Actions pipeline end-to-end
Verified CloudWatch monitoring and alarms

## Challenges & Fixes

### Challenge 1

One of the backend targets behind the ALB was unhealthy.

**Diagnosis:** Checked the target health and the ALB health checks

**Fix:** Fixed the backend target configuration and verified it was healthy

**What I learned about:** How the health checks and target health work in ALB

## Lessons learned

How to deploy containerized applications on AWS
How ALB, Target Groups and Auto Scaling work together
How to use GitHub Actions and CloudWatch for deployment and monitoring

## Improvements

Private application subnets
HTTPS with ACM + Route 53
More restrictive IAM policies
Better monitoring/logging
Infrastructure as Code (Terraform)

## Run it locally

```bash
docker build -t aws-web-app .
docker run -d -p 8080:80 --name aws-web-app aws-web-app
```

## Security

This repository contains no AWS secrets such as credentials, private keys, or passwords.

## Content warning

The index.html file that's used as the content for the demo website in this project is just a placeholder - it's not a custom web design. This is a project about deploying Docker containers to AWS, not about web design.

## Cost disclaimer

I only created AWS resources for the duration of this project and make sure to clean them up when they were no longer needed.
