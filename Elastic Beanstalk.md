# Elastic Beanstalk

## General Information

- Quickly deploy and manage web-apps on AWS
- It's a PaaS (Platform as a service)
- AWS says it's not recommended for "production" applications
	- For enterprise or very large companies
- Elastic Beanstalk is powered by a CloudFormation template which can setup for you
	- Elastic Load Balancer
	- Autoscaling Groups
	- RDS Database
	- EC2 Instance
	- Monitoring (Cloudwatch, SNS)
	- In-Place and Blue/Green deployment methodologies
	- Security (Rotates passwords)
	- Can run Dockerized environments.
- 