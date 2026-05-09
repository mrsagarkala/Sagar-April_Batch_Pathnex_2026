
Rewrite ALL FOUR from scratch:

1. Ansible: Install nginx
2. Terraform: EC2 (choose any Pathnex instance)
3. Kubernetes: Deployment 2 replicas
4. Shell: Print date + uptime

Set a timer: **20 minutes**




pipeline {
    agent any
    parameters {
        string(name: 'ENVIRONMENT', defaultValue: 'dev', description: 'Deployment Environment')
    }
    environment {
        INSTITUTE_NAME = "Pathnex"
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Pathnex/sample-java-app.git'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo "Deploying to $ENVIRONMENT by $INSTITUTE_NAME"'
            }
        }
    }
}


stages:
  - deploy

variables:
  INSTITUTE_NAME: "Pathnex"
  ENVIRONMENT: "dev"

deploy:
  stage: deploy
  image: alpine:latest
  script:
    - echo "Deploying to $ENVIRONMENT by $INSTITUTE_NAME"
