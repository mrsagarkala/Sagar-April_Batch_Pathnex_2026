
Complete these steps:


- VPC
- Subnet
- Internet gateway
- Route table
- EC2 (c5.xlarge / r5.2xlarge / r6i.4xlarge / c6i.8xlarge / c6a.12xlarge)







pipeline {
    agent any
    environment {
        INSTITUTE_NAME = "Pathnex"
    }
    triggers {
        cron('H 2 * * *') // every day at 2 AM
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Pathnex/sample-java-app.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}


stages:
  - build

build:
  stage: build
  image: maven:3.8.1-jdk-17
  script:
    - git clone https://github.com/Pathnex/sample-java-app.git
    - cd sample-java-app
    - mvn clean package
