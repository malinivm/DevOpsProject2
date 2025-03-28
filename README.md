# Containerized Application Deployment on AWS ECS

## Overview
This project demonstrates the deployment of a Python-based web application on **AWS Elastic Container Service (ECS) using Fargate**. The application is **containerized with Docker**, stored in **AWS Elastic Container Registry (ECR)**, and deployed through an **automated CI/CD pipeline with Jenkins**.

## Tech Stack
- **AWS ECS (Fargate)** – Serverless container orchestration  
- **AWS ECR** – Container image storage  
- **Docker** – Containerization  
- **Jenkins** – CI/CD automation  
- **Python** – Web application  

## Features
✅ **Containerizes a Python-based web application using Docker**  
✅ **Pushes Docker images to AWS ECR**  
✅ **Automates builds and deployments via Jenkins**  
✅ **Deploys the application on AWS ECS (Fargate) for scalability and efficiency**  

## Architecture
1. **Code Commit** – Changes are pushed to the GitHub repository.  
2. **Jenkins Build Trigger** – Jenkins pipeline detects changes and triggers a new build.  
3. **Docker Image Build & Push** – Jenkins builds the image and pushes it to AWS ECR.  
4. **Deployment to AWS ECS** – The new container image is deployed to ECS Fargate.  

## Setup Instructions

### Prerequisites
- AWS CLI installed and configured  
- Docker installed  
- Jenkins set up with necessary plugins  
- AWS IAM roles for ECS, ECR, and Jenkins  

### Steps
1. **Clone the repository:**
   git clone https://github.com/your-repo/ecs-deployment.git
   cd ecs-deployment
2. __Build the Docker image:__
   docker build -t your-app .
3. __Authenticate Docker with AWS ECR:__
   aws ecr get-login-password --region your-region | docker login --username AWS --password-stdin your-account-id.dkr.ecr.your-region.amazonaws.com
4. __Push the Docker image to AWS ECR:__
   docker tag your-app:latest your-account-id.dkr.ecr.your-region.amazonaws.com/your-repo:latest
   docker push your-account-id.dkr.ecr.your-region.amazonaws.com/your-repo:latest
5. __Deploy to ECS Fargate:__
   Update ECS Task Definition with the new image.
   Update ECS Service to use the new task definition.

## Conclusion
This project showcases a fully automated pipeline for deploying a containerized Python web application on AWS ECS Fargate. It leverages Docker, AWS ECR, and Jenkins to ensure smooth deployments and scalability.
