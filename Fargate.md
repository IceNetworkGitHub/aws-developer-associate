# Fargate

- **Fargate** is **Serverless containers**. Don't worry about servers. Run containers, and pay based on duration and consumption
  - Fargate has **Cold Starts** so if this is an issue for you then use ECS
  - **Duration** As long as you want
  - **Memory** Up to 30 GB
  - **Pricing** Pay at least 1 min and every additional second

## Fargate Tasks

- In your Fargate Task Definition, you **define** the **memory** and **vCPU**
- You will then add your containers and **allocate** the memory and vCPU required for each
- When you run the Task, you can choose what VPC and subnet it will run in
- **Apply a Security Group to a Task**
- Apply an IAM role to the Task
- You can apply SG and IAM role for both ECS and Fargate Tasks and Services
