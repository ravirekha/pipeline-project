pipeline {
  environment {
    registry = "vijaylokesh/test1"
    registryCredential = 'docker-hub'
    dockerImage = ''
  }
  agent {
  label 'docker_slave1'
  }
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/ravirekha/pipeline-project.git'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":latest"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '','docker-hub') {
            dockerImage.push()
          }
        }
      }
    }
  }
} 
