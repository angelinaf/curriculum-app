pipeline {
  agent any
  stages {
    stage('check out code') {
      steps {
        git(url: 'https://github.com/angelinaf/curriculum-app', branch: 'dev')
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f curriculum-front/Dockerfile . -t angelinaf/jenkins-course'
      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'angelinaf'
        DOCKERHUB_PASSWORD = '8nXrPgKHiU8V!TA'
      }
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('push') {
      steps {
        sh 'docker push angelinaf/jenkins-course:tagname'
      }
    }

  }
}