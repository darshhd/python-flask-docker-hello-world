pipeline {
  environment {
    registry = "darshhd/python-hello-world"
    registryCredential = 'docker-hub'
    dockerImage = 'python-hello-world'
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/darshhd/python-flask-docker-hello-world.git'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }

