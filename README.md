🚀 3-Tier Application Deployment on AWS EKS using GitLab CI/CD

📌 Overview

This project demonstrates the end-to-end deployment of a 3-tier web application using Docker, GitLab CI/CD, AWS EKS, and AWS ECR.

The goal of this project is to simulate a real-world CI/CD workflow by automating:

Application build

Testing

Container image publishing

Kubernetes deployment

🏗 Architecture

The application follows a 3-tier architecture:

Frontend (Presentation Layer)

React.js

Served as a Docker container

Backend (Application Layer)

Node.js (REST API)

Dockerized service

Database (Data Layer)

MongoDB

Deployed as a Kubernetes workload

All components run on AWS EKS (Kubernetes).

🛠 Tech Stack
Application

React.js

Node.js

MongoDB

DevOps / Cloud

Docker

GitLab CI/CD

AWS EKS

AWS ECR

AWS IAM

Kubernetes (kubectl)

📂 Repository Structure
.
├── Application-Code/
│   ├── frontend/
│   │   └── Dockerfile
│   ├── backend/
│   │   └── Dockerfile
│
├── k8s-manifests/
│   ├── frontend/
│   │   └── deployment.yml
│   ├── backend/
│   │   └── deployment.yml
│   └── mongo/
│       └── deployment.yml
│
├── .gitlab-ci.yml
└── README.md

🔄 CI/CD Pipeline Flow

The pipeline is triggered on pushes to the main branch.

Pipeline Stages

Test

Runs unit tests for frontend and backend

Ensures code quality before deployment

Build & Push

Builds Docker images for frontend and backend

Tags images using Git commit SHA

Pushes images to AWS ECR

Deploy

Updates Kubernetes manifests with new image tags

Deploys application to AWS EKS using kubectl

🧪 CI/CD Pipeline Diagram
Code Push (main)
      ↓
Run Tests
      ↓
Build Docker Images
      ↓
Push Images to AWS ECR
      ↓
Deploy to AWS EKS

🔐 Authentication & Security

AWS credentials are stored securely using GitLab CI/CD variables

No secrets are hardcoded in the repository

AWS CLI uses environment variables for authentication

EKS access is handled via IAM-based authentication

📦 Docker Image Strategy

Images are tagged using commit SHA

Ensures immutable and traceable deployments

Avoids use of the latest tag

Example:

frontend-app:37084c75
backend-app:37084c75

☸ Kubernetes Deployment

Kubernetes manifests are used for deployment

Image tags are dynamically injected during CI/CD

Deployments are applied recursively across service directories

kubectl apply -R -f k8s-manifests/

🚀 How to Deploy (CI/CD)

Push code to the main branch

GitLab CI/CD automatically:

Runs tests

Builds & pushes images to ECR

Deploys the application to EKS

No manual intervention required.

🧠 Key Learnings from This Project

Designing CI/CD pipelines using GitLab

Containerizing full-stack applications

Handling Docker-in-Docker in CI

Managing AWS authentication in pipelines

Deploying applications to Kubernetes (EKS)

Debugging real-world CI/CD and Kubernetes issues

🔮 Future Improvements

Add Helm charts for Kubernetes deployments

Implement image vulnerability scanning

Add staging and production environments

Introduce rollback and health-check automation

Add monitoring with Prometheus and Grafana
