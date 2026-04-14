# AWS Blue/Green Deployment
# 📌 Overview
This project demonstrates a Blue/Green Deployment strategy on AWS to enable safe application realeases with minimal downtime.

Two seperate environments (Blue = current production, Green = new version) were deployed behind an Application Load Balancer (ALB), allowing traffic shifting and rollback capability.

# 🎯 Project Goals
- Implement a Blue/Green deployment architecture
- Achieve near zero-downtime deployments
- Validate application health before traffic switching
- Simulate a real-world production deployment workflow
- Demonstrate troubleshooting and debugging skills in AWS

# 🏗️ Architecture
- Application Load Balancer (ALB)
- Blue Target Group (v1 - production)
- Green Target Group (v2 - new version)
- EC2 instances (Apache web server)
- Security Groups
- Health Checks

# ⚒️ Services Used
- Amazon EC2
- Application Load Balancer (ALB)
- Target Groups
- Auto Scaling Groups
- IAM
- Security Groups
- User Data (Bash Scripting)

# 🚀 Deployment Workflow
1. Deploy Blue Environment (Production)
- Launched EC2 Instances
- Installed Apache via User Data
- Registered Instances in Blue target group

2. Configure Application Load Balancer
- Created ALB
- Attached Blue target group
- Configured Listener on port 80

3. Deploy Green Environment (New Version)
- Launched new EC2 isntances with updated version
- Registered EC2 instances in Green target group

4. Perform Health Checks
- Verified Green environment passed ALB health checks
- Ensured instances returned HTTP 200 responses

5. Shift Traffic to Green Environment
- Updated ALB listener rules to forward traffic to Green target group

6. Validate Deployment
- Confirmed new version via ALB DNS
- Verified application functionality

# 🔙 Rollback Strategy
If issues are detected:
- Switch ALB listener back to Blue target group
- Restore previous stable environment instantly

# ⚠️ Challenges & Solutions
Issue: ALB returning 502 Bad Gateway
- Cause: Web server not fully initialized or misconfigured
- Fix: Verified Apache installation in user data and ensured service started properly

Issue: Target Group Health Checks Failing
- Cause: Security Group rules blocking traffic or incorrect health check path
- Fix: Updated Security Groups and confirmed HTTP endpoint returned 200

# 🧠 Key Skills Demonstrated
- AWS networking and load balancing
- Blue/Green deployment strategy
- Infrastructure troubleshooting and debugging
- Linux server configuration with user data
- Application health validation and monitoring

# 🚀 Future Improvements
- Automate infrasturcture using Terraform
- Implement AWS CodeDeploy for automated Blue/Green deployments
- Add CI/CD pipeline
- Integrate CloudWatch Monitoring & Alerts
- Use Route53 weighted routing for gradual traffic shifting

# 📸 Full Screenshot walkthrough
- Additional screenshots can be found in the /screenshots directory



