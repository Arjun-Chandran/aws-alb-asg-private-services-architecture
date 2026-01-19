# aws-alb-asg-private-services-architecture

A highly available and scalable AWS infrastructure architecture designed for a Java web application.  
This project demonstrates how to deploy an application using **Application Load Balancer (ALB)** and **Auto Scaling Groups (ASG)**, while keeping backend services isolated in private networks.

This project was implemented as part of a **hands-on AWS infrastructure course**, with full deployment, configuration, and customization performed to understand real-world AWS design patterns.

---

## Architecture Overview

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/e02835ab-0a6b-4aff-bf11-da72e9384ef5" />


The architecture follows AWS best practices for **high availability, scalability, and security**:

- Public-facing traffic handled by an Application Load Balancer
- Auto Scaling group of EC2 instances running Tomcat
- Backend services deployed in private subnets
- Internal service communication using Route 53 Private Hosted Zones
- Strict security group separation between tiers

---

## Core Components

- **DNS**
  - GoDaddy (public DNS)
  - Amazon Route 53 (public & private hosted zones)

- **Compute**
  - EC2 instances (Tomcat)
  - Auto Scaling Group

- **Load Balancing**
  - Application Load Balancer (HTTPS → HTTP 8080)

- **Backend Services (Private)**
  - MySQL
  - RabbitMQ
  - Memcached

- **Storage**
  - Amazon S3 (application artifacts / backups)

- **Networking & Security**
  - Separate security groups for ALB, application tier, and backend tier
  - Private DNS resolution for backend services

---

## Traffic Flow

1. Users access the application via a public domain
2. DNS resolves to the Application Load Balancer
3. ALB forwards traffic to Tomcat instances in the Auto Scaling Group
4. Application communicates with backend services using private DNS names
5. Backend services remain inaccessible from the public internet

---

## Key Learning Outcomes

- Designing highly available AWS architectures
- Using ALB and Auto Scaling for horizontal scalability
- Securing backend services using private subnets and security groups
- Internal service discovery with Route 53 private hosted zones
- Automating EC2 provisioning using userdata scripts

---

## Notes

- This project focuses on **infrastructure design and deployment**
- Not intended as a production-ready setup
- No Infrastructure-as-Code (Terraform/CloudFormation) included yet

---

## Future Improvements

- Add Terraform or CloudFormation
- Add monitoring using CloudWatch
- Add CI/CD deployment pipeline
- Convert backend services to managed AWS services (RDS, ElastiCache)

---

## License

This project is intended for **educational and learning purposes**.

