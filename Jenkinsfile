pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/karnatisrinivas/curriculum-app', branch: 'dev')
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f curriculum-front/Dockerfile '
      }
    }

    stage('Log into Dockerhub') {
      environment {
        DOCKERHUB_USER = 'srinivaskarnati'
        DOCKERHUB_PASSWORD = 'SRInivas@123'
      }
      steps {
        sh 'docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

    stage('Push') {
      steps {
        sh 'docker push srinivaskarnati/curriculum-front:latest'
      }
    }

  }
}
