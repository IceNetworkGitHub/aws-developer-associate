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
	- Can run Dockerized environments

## Web Vs Worker Environment
- **Web** application uses the Web Environment and there are two types of Web Environment
	- **Load Balanced Env**
		- Uses ASG and set to scale
		- Uses an ELB
		- Designed to scale
	- **Single Instance Environment**
		- Still uses an ASG but Desired Capacity is set to 1, to ensure the server is always running
		- No ELB to save cost
		- Public IP address has to be used to route traffic to server

- **Worker** application uses the Worker Environment
	- It creates the following:
		- ASG
		- SQS queue
		- Installs Sqsd daemon on the EC2 instances
		- Creates CloudWatch Alarm to dynamically scale instances based on health