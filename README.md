# Deploy Grafana on Amazon ECS (Fargate)
In this project, I deployed Grafana on Amazon ECS using the Fargate launch type. This project focused on containerization and orchestration with Docker and ECS, demonstrating the ability to run monitoring applications in a scalable, serverless container environment.

**Project Architecture**
<img width="1536" height="1024" alt="grafana 2" src="https://github.com/user-attachments/assets/de8ebaac-5827-43c7-8f93-34a45eef857d" />

**Architecture Overview**
- Amazon ECS (Fargate) - Runs the Grafana container without managing servers.
- ECS Task Definition - Defines Grafana container settings (image, port 3000).
- ECS Service - Ensures Grafana task stays running and manages scaling.
- Security Group - Allows inbound traffic on port 3000 (TCP) for Grafana UI.
- VPC and Subnets - Provides networking for ECS tasks.
- Public IP - Auto-assigned to access Grafana externally.
- Grafana UI - Accessible at http://<my-public-ip>:3000 after deployment.

 **☁️ AWS Services Used**
 - **Amazon ECS (Fargate)** → Serverless container orchestration for running Grafana  
- **Amazon Elastic Container Registry (ECR)** → Hosted the Grafana Docker image  
- **Amazon VPC** → Provided the networking environment (subnets, routing)  
- **Amazon IAM** → Managed permissions and roles for ECS tasks  
- **Amazon CloudWatch** → Monitored logs from ECS tasks  
- **Amazon Security Groups** → Controlled inbound/outbound traffic (port 3000 open for Grafana)

**Steps I Followed**
1. Create Security Group
- Created a new security group for ECS tasks.
- Allowed inbound traffic on port 3000 (TCP) to access Grafana UI.
- Outbound rules left as default (allow all).

2. Create ECS Cluster
- Launched a new ECS cluster using the Fargate launch type.
- Selected default VPC and subnets.

3. Register Task Definition
- Created a new ECS task definition for Grafana.
- Container details:
- Image: grafana/grafana:latest
- Port mapping: 3000/TCP
- Assigned the ecsTaskExecutionRole IAM role for task execution.

4. Deploy Service
- Created an ECS service from the task definition.
- Chose Fargate as the launch type.
- Deployed the service with 1 task.
- Assigned the ECS security group to allow external access on port 3000.
- Enabled auto-assign public IP so Grafana could be reached from the browser.

5. Access Grafana
- Retrieved the public IP of the running ECS task.
- Accessed Grafana(this is the live grafana UI)
<img width="1916" height="995" alt="Grafana login page" src="https://github.com/user-attachments/assets/7e007472-600f-46d1-bba6-fa5539ec2049" />

**Outcome**
**Successfully deployed Grafana on Amazon ECS Fargate**
- This project strengthened my skills in:
- Docker container deployment on ECS
- Fargate serverless container management
- IAM roles for ECS tasks
- Security group configuration for application access






