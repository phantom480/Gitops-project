# 🚀 End-to-End GitOps CI/CD Pipeline on AWS EKS using Jenkins, Nexus, SonarQube, Trivy & ArgoCD

![AWS](https://img.shields.io/badge/AWS-EKS-orange?logo=amazonaws)
![Terraform](https://img.shields.io/badge/Terraform-IaC-623CE4?logo=terraform)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes)
![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker)
![Jenkins](https://img.shields.io/badge/Jenkins-CI/CD-D24939?logo=jenkins)
![Nexus](https://img.shields.io/badge/Nexus-Repository-4CAF50)
![SonarQube](https://img.shields.io/badge/SonarQube-Code%20Quality-blue?logo=sonarqube)
![Trivy](https://img.shields.io/badge/Trivy-Security-success)
![ArgoCD](https://img.shields.io/badge/ArgoCD-GitOps-orange)

---

## 📖 Project Overview

This project demonstrates a **Production-Ready GitOps CI/CD Pipeline** deployed on **AWS EKS**.

The complete infrastructure is provisioned using **Terraform**. The application is built using **Jenkins**, artifacts are stored in **Nexus Repository Manager**, source code quality is analyzed using **SonarQube**, security scans are performed using **Trivy**, Docker images are built and pushed to **Docker Hub**, and **ArgoCD** automatically deploys the application into **Amazon EKS** following GitOps principles.

---

# 🏗 Architecture

```text
                    Developer
                        │
                        ▼
                GitHub Repository
                        │
                        ▼
                 Jenkins Pipeline
                        │
        ┌───────────────┼────────────────┐
        │               │                │
        ▼               ▼                ▼
 Maven Build      SonarQube Scan   Trivy FS Scan
        │
        ▼
 Upload Artifact
        │
        ▼
 Nexus Repository
        │
        ▼
 Docker Build
        │
        ▼
 Trivy Image Scan
        │
        ▼
 Docker Hub
        │
        ▼
 Update Kubernetes Manifest
        │
        ▼
 GitOps Repository
        │
        ▼
 ArgoCD
        │
        ▼
 Amazon EKS Cluster
```

---

# ⚙️ Tech Stack

## Cloud
- AWS EC2
- AWS EKS
- IAM
- VPC

## Infrastructure as Code
- Terraform

## CI/CD
- Jenkins

## Artifact Repository
- Nexus Repository Manager

## Code Quality
- SonarQube

## Security
- Trivy

## Containerization
- Docker

## Container Orchestration
- Kubernetes (Amazon EKS)

## GitOps
- ArgoCD

## Build Tool
- Maven

## Version Control
- Git
- GitHub

## Application
- Java Spring Boot

---

# 📂 Repository Structure

```
GitOps-CI-CD/
│
├── terraform/
│   ├── eks/
│   ├── vpc/
│   ├── iam/
│   └── security-groups/
│
├── kubernetes/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── ingress.yaml
│
├── application/
│
├── Jenkinsfile
│
├── Dockerfile
│
├── README.md
│
└── images/
```

---

# 🚀 CI/CD Pipeline Workflow

## 1. Source Code Checkout

- Pull latest code from GitHub

---

## 2. Build Application

- Compile Java application
- Package JAR using Maven

---

## 3. Unit Testing

- Execute Maven Tests

---

## 4. Upload Artifact

- Upload generated JAR file to Nexus Repository

---

## 5. Static Code Analysis

- Analyze source code using SonarQube

---

## 6. Quality Gate Validation

- Verify project quality before deployment

---

## 7. File System Security Scan

- Scan source code using Trivy

---

## 8. Docker Image Build

- Build Docker image

---

## 9. Docker Image Security Scan

- Scan Docker image using Trivy

---

## 10. Push Docker Image

- Push image to Docker Hub

---

## 11. Update Kubernetes Manifest

- Update deployment image tag

---

## 12. Push GitOps Repository

- Commit updated Kubernetes manifests

---

## 13. ArgoCD Synchronization

- Detect Git changes
- Sync application automatically

---

## 14. Deploy to Amazon EKS

- Rolling Update
- Self-Heal
- Auto Sync

---

# 📸 Project Screenshots

## ☁ AWS Infrastructure

Provisioned EC2 Instances for Jenkins, Nexus and Kubernetes Worker Nodes.

![AWS Infrastructure](images/01-ec2-instance.png)

---

## 📦 Nexus Repository Manager

Artifact Repository used for storing application packages.

![Nexus](images/02-nexus-dashboard.png)

---

## ⚙ Jenkins Pipeline

Successful CI/CD Pipeline Execution.

![Jenkins Pipeline](images/03-jenkins-pipeline.png)

---

## 🔍 SonarQube Dashboard

Project Code Quality Report.

![Sonar Dashboard](images/04-sonarqube-dashboard.png)

---

## 📊 SonarQube Issues

Detected Bugs, Code Smells and Security Hotspots.

![Sonar Issues](images/05-sonarqube-issues.png)

---

## ☸ ArgoCD Components

ArgoCD Components Running inside Kubernetes.

![ArgoCD Components](images/06-argocd-components.png)

---

## 🚀 ArgoCD Dashboard

GitOps Application Deployment Dashboard.

![ArgoCD UI](images/07-argocd-ui.png)

---

# 🔄 Complete DevSecOps Workflow

```
Developer
     │
     ▼
GitHub Repository
     │
     ▼
Jenkins Pipeline
     │
     ├────────► Maven Build
     │
     ├────────► Nexus Repository
     │
     ├────────► SonarQube Analysis
     │
     ├────────► Trivy File Scan
     │
     ├────────► Docker Build
     │
     ├────────► Trivy Image Scan
     │
     ├────────► Docker Hub
     │
     └────────► GitOps Repository
                      │
                      ▼
                  ArgoCD
                      │
                      ▼
                 Amazon EKS
```

---

# ✨ Features

- Infrastructure as Code using Terraform
- Amazon EKS Cluster Deployment
- Jenkins CI/CD Pipeline
- Nexus Artifact Repository
- Maven Build Automation
- SonarQube Static Code Analysis
- Trivy Security Scanning
- Docker Image Build & Push
- GitOps Deployment with ArgoCD
- Automated Kubernetes Deployment
- Self-Healing Applications
- Auto Synchronization
- Production-Ready DevSecOps Pipeline

---

# 📚 Prerequisites

- AWS Account
- Terraform
- kubectl
- eksctl
- Docker
- Git
- Java 17+
- Maven
- Jenkins
- SonarQube
- Nexus Repository Manager
- Trivy
- ArgoCD

---

# 🚀 Deployment Steps

```bash
# Clone Repository
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git

cd YOUR_REPOSITORY

# Deploy Infrastructure
terraform init
terraform plan
terraform apply

# Configure kubectl
aws eks update-kubeconfig --region <region> --name <cluster-name>

# Verify Cluster
kubectl get nodes

# Install ArgoCD
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# Access ArgoCD
kubectl get svc -n argocd
```

---

# 📈 Future Improvements

- Helm Charts
- Prometheus Monitoring
- Grafana Dashboards
- AWS Load Balancer Controller
- Horizontal Pod Autoscaler
- External Secrets
- HashiCorp Vault Integration
- GitHub Actions Pipeline
- Blue/Green Deployment
- Canary Deployment

---

# 👨‍💻 Author

**Mohd Aarif**

Cloud & DevOps Engineer

### GitHub

https://github.com/phantom480

### LinkedIn

www.linkedin.com/in/mohd-aarif-1637682aa

---

## ⭐ Support

If you found this project helpful, please consider giving it a ⭐ on GitHub.

It motivates me to build more Cloud and DevOps projects.
