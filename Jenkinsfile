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
          def customImage = docker.build("my-image:${env.BUILD_ID}")
        }
        echo "Build the image!!"
      }
        
    }
     
     stage('Deploy Image') {
      steps {
       srcipt {
        docker.withRegistry( '', registryCredential) {
         dockerImage.push()
        }
       }
      }
     }
  }
}
    
  
