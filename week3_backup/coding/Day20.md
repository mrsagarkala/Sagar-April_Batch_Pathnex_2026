
Fix these intentionally broken files:


- name Install stuff
  hosts all
  tasks:
   -name: install
    yum:
      name httpd
      state present



resource aws_instance "Bad" {
 ami "ami-123"
 instance_type c6i.8xlarge
}



apiVersion apps/v1
kind Deployment
metadata:
 name broken-app
spec:
replicas:3
selector:
 matchLabels:
   app: broken
template:
 metadata:
  labels:
   app: broken
 spec:
  containers:
   -name: app
    image nginx




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
        stage('Use Secret') {
            steps {
                withCredentials([string(credentialsId: 'PATHNEX_API_KEY', variable: 'API_KEY')]) {
                    sh 'echo "Using secret $API_KEY for $INSTITUTE_NAME"'
                }
            }
        }
    }
}


stages:
  - build

variables:
  INSTITUTE_NAME: "Pathnex"
  API_KEY: "PLACEHOLDER_SECRET"

build:
  stage: build
  image: alpine:latest
  script:
    - echo "Using secret $API_KEY for $INSTITUTE_NAME"
