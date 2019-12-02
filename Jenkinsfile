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
          echo "Cloning Git"
          git 'https://github.com/diksha-gupta04/docker.git'
          echo "Cloning done!"
        }
      }
      
      stage('Building image') {
      steps{
        echo "Building image"
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }
        echo "Build the image!!"
      }
    }
  }
}
    
  
