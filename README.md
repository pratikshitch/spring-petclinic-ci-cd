# CI/CD Pipeline with Jenkins + Docker + AWS + SonarQube

## 🧩 Stack
- Jenkins (Master-Slave)
- GitHub
- Docker + DockerHub
- SonarQube
- AWS EC2, Custom VPC, Subnets
- Maven

## 📋 Pipeline Steps
1. Git Clone from GitHub
2. SonarQube Code Quality Check
3. Build Java Project with Maven
4. Create and Push Docker Image
5. Deploy to EC2 using SSH

## 📌 AWS Architecture
- VPC with public/private subnets
- Jenkins Master on Public EC2
- Slave and App EC2 in private subnet
- SonarQube in Public Subnet
- Auto Scaling Group with Load Balancer

## 📸 Screenshots
![Architecture](images/architecture-diagram.png)

## 🛠️ Setup Scripts
See [`setup/`](./setup) folder for EC2 installation and AWS setup
