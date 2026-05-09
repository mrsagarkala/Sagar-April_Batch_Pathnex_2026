

---
- name: Install MariaDB for Pathnex
  hosts: all
  become: yes

  tasks:
    - name: Install MariaDB
      yum:
        name: mariadb-server
        state: present

    - name: Start MariaDB
      service:
        name: mariadb
        state: started
        enabled: yes



resource "aws_instance" "PathnexServer" {
  ami           = "ami-0abcd1234abcd1234"
  instance_type = "r5.2xlarge"

  tags = {
    Name = "Pathnex-Output-EC2"
  }
}

output "PathnexPublicIP" {
  value = aws_instance.PathnexServer.public_ip
}



apiVersion: v1
kind: Pod
metadata:
  name: pathnex-sidecar
spec:
  containers:
    - name: main
      image: nginx
    - name: sidecar
      image: busybox
      command: ["sh", "-c", "echo Sidecar running; sleep 3600"]



#!/bin/bash

greet() {
  echo "Welcome to Pathnex DevOps Training"
}

greet





pipeline {
    agent any
    environment {
        INSTITUTE_NAME = "Pathnex"
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
    post {
        success {
            mail to: 'team@pathnex.com',
                 subject: "SUCCESS: Build #${env.BUILD_NUMBER}",
                 body: "Build completed successfully for $INSTITUTE_NAME"
        }
        failure {
            mail to: 'team@pathnex.com',
                 subject: "FAILURE: Build #${env.BUILD_NUMBER}",
                 body: "Build failed for $INSTITUTE_NAME"
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
  after_script:
    - echo "Sending notification email to team@pathnex.com"
