pipeline {
  environment {
    registry = "dikshagupta04/docker-test"
    registryCredential = 'dockerhub'
  }
  agent {
    dockerfile true
  }
    stages {
      stage('Clone repository') {
        steps {
        checkout scm
        }
      }
      
      stage('Building image') {
      steps{
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
  }
}
    
  
