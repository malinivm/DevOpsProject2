pipeline {
    agent any
    environment {
        AWS_REGION = "us-east-1"
        ECR_REPO = "578979060653.dkr.ecr.${AWS_REGION}.amazonaws.com/app"
    }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/malinivm/DevOpsProject2.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-project2 .
'
            }
        }
        stage('Authenticate to ECR') {
            steps {
                sh 'aws ecr get-login-password --region $AWS_REGION | docker login --username AWS --password-stdin $ECR_REPO'
            }
        }
        stage('Push Image to ECR') {
            steps {
                sh 'docker tag devops-project2:latest $ECR_REPO:latest'
                sh 'docker push $ECR_REPO:latest'
            }
        }
        stage('Deploy to ECS') {
            steps {
                sh 'aws ecs update-service --cluster ecs-cluster --service python-service --force-new-deployment'
            }
        }
    }
}
