# aws-self-healing-scalable-infrastructure

<img width="1199" height="669" alt="self-healing" src="https://github.com/user-attachments/assets/5cf15f5d-8f01-463b-8dee-a23853b8b6f0" />

High Availability, Scalability, Cost-Optimization

<img width="1366" height="768" alt="lunch" src="https://github.com/user-attachments/assets/90c9753a-be05-4bf9-8059-07196b344157" />
<img width="1366" height="768" alt="png h" src="https://github.com/user-attachments/assets/d8ecfa27-f1df-4148-be3f-0115ac583440" />
📌 Project Overview
In a modern production environment, downtime equals lost revenue. This project demonstrates a highly available, self-healing infrastructure built on AWS. By leveraging Auto Scaling Groups (ASG) and Application Load Balancers (ALB), I designed a system that automatically detects instance failure, replaces unhealthy nodes, and scales resources dynamically based on real-time traffic demand.

🎯 Key Objectives
Zero Downtime: Automated replacement of "unhealthy" instances.
Elasticity: Scaling out during traffic spikes and scaling in during quiet hours to save costs.
High Availability: Distributing traffic across multiple Availability Zones.

🏗️ Architecture & Tech Stack
Compute: Amazon EC2, Amazon Machine Image (AMI)
Scaling & Recovery: AWS Auto Scaling Group (ASG)
Traffic Management: Application Load Balancer (ALB)
Monitoring: Amazon CloudWatch, SNS (Simple Notification Service)
Networking: Amazon VPC, Security Groups

🚀 Step-by-Step Implementation
1. Golden Image Creation (AMI)
I configured a base EC2 instance with all necessary application dependencies and converted it into an Amazon Machine Image (AMI). This ensures that every new instance launched by the Auto Balancer is an exact, pre-configured replica of the production environment.

2. Infrastructure Automation with Launch Templates
I defined a Launch Template to standardize the deployment. This includes:

Instance type (e.g., t2.micro for cost-efficiency).
Security Group rules (Port 80 for Web, Port 22 for SSH).
User Data scripts for automated startup tasks.

3. Self-Healing Configuration
I implemented a Target Group and Health Checks.
The "Self-Healing" Logic: The ALB performs frequent "pings" to the application. If an instance fails to respond, the Auto Scaling Group terminates it and launches a fresh instance automatically to maintain the Desired Capacity.

4. Dynamic Scaling Policies
To optimize costs, I configured CloudWatch Alarms:
Scale-Out: When CPU Utilization exceeds 70%, a new instance is added.
Scale-In: When CPU drops below 30%, extra instances are removed to prevent unnecessary AWS costs.

🧪 Testing & Validation
Failure Simulation: I manually terminated a running instance via the AWS Console.
Result: The ASG detected the "Unhealthy" state within 60 seconds and provisioned a replacement instance without manual intervention.
Load Testing: Used stress-testing tools to spike CPU usage.

💡 Key Lessons Learned
Infrastructure as Code: Realized the importance of Launch Templates for version control in infrastructure.
Health Check Grace Periods: Learned to set an appropriate "warm-up" time so the system doesn't kill an instance before it finishes booting up.
Cost Management: Balanced performance and cost by using "Target Tracking" policies.

🛠️ How to Replicate This
Clone this repository.
Follow the detailed Documentation/Guide.md provided in the docs folder.
Use the provided user-data.sh script to bootstrap your EC2 instances.

👨‍💻 Connect with Me
LinkedIn: kolade segun Adekunle 
Portfolio: https://github.com/Engineersegun
Email:koladesegun18@gmail.com
