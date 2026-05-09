

---
- name: Update SSH config for Pathnex
  hosts: all
  become: yes

  tasks:
    - name: Disable root login
      lineinfile:
        path: /etc/ssh/sshd_config
        regexp: "^PermitRootLogin"
        line: "PermitRootLogin no"



resource "aws_key_pair" "PathnexKey" {
  key_name   = "PathnexKey"
  public_key = file("~/.ssh/id_rsa.pub")
}

output "Pathnex_Key_Name" {
  value = aws_key_pair.PathnexKey.key_name
}



apiVersion: v1
kind: Pod
metadata:
  name: pathnex-sidecar
spec:
  containers:
    - name: app
      image: nginx
    - name: log-writer
      image: busybox
      command: ["sh", "-c", "while true; do echo log entry; sleep 5; done"]



#!/bin/bash

DIR="/var/log"

COUNT=$(ls $DIR | wc -l)

echo "Total files in $DIR: $COUNT"




pipeline {
    agent any
    environment {
        INSTITUTE_NAME = "Pathnex"
        TEAM = "DevOps"
        ENV = "staging"
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Pathnex/sample-java-app.git'
            }
        }
        stage('Build') {
            steps {
                sh '''
                if [ -d ".m2" ]; then
                    echo "Using cached dependencies for $INSTITUTE_NAME in $ENV by $TEAM"
                else
                    mvn clean compile
                fi
                '''
            }
        }
    }
}


stages:
  - build

variables:
  INSTITUTE_NAME: "Pathnex"
  TEAM: "DevOps"
  ENV: "staging"

build:
  stage: build
  image: maven:3.8.1-jdk-17
  cache:
    key: "${ENV}-maven-cache"
    paths:
      - .m2/repository
  script:
    - mvn clean compile
    - echo "Cached dependencies for $INSTITUTE_NAME in $ENV by $TEAM"
