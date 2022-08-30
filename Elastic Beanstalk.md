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

---

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

---

## Deployment Policies

| Deployment Policy  | Load Balanced Env   | Single Instance Env   |
|---|---|---|
| All at once  | V   | V   |
| Rolling   | V  | X  |
| Rolling with additional batch  | V  | X |
| Immutable  | V  | V  |

- **Rolling and Rolling with additional batch requires** an ELB because it attaches and detaches instances in batches from the ELB

### EB - All At Once
1) Deploys the new app version to all instances at the same time
2) Takes all instances **out of service** while the deployment processes
3) Servers become available again
4) The fastest but also the most dangerous deployment method

### Rolling
1) Deployes the new app version to a batch of instances at a time.
2) Take batch's instances **out of service** while the deployment processes.
3) Reattachs updated instances
4) Goes onto next batch, taking them out of service
5) Reattaches those instances (rinse and repeat)

### Rolling With Additional Batch
1) Launch new instances that will be used to replace a batch
2) Deploy update app version to new batch
3) Attach the new batch and terminate the existing batch
4) Rolling with Additional Batch's ensure our capacity is never reduced. This is important for applications where a reduction in capacity could cause availability issues for users.

### Immutable
1) 