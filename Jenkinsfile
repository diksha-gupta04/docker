pipeline {
  environment {
    registry = "dikshagupta04/docker-test"
    registryCredential = 'dockerhub'
  }
  agent {
    dockerfile true
  }
    stages {
      stage('Cloning Git') {
        steps {
          git 'https://github.com/diksha-gupta04/docker.git'
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
    
  
