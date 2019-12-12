pipeline {
 environment {
    registry = "dikshagupta04/docker-test"
    registryCredential = 'dockerhub'
  }
 
  agent any
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
     
     stage('Download') {
      steps {
       sh 'echo "arctifact file" > generatedFile.txt'
      }
     }
     
    }
    
    post {
     
      success {
      
      emailext (
       
         subject: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
          body:  '${FILE,path="myfile.html"}', 
          recipientProviders: [[$class: 'DevelopersRecipientProvider']],
       to: 'diksha2547@gmail.com'
       
        )
    }

   
    failure {
    
      emailext (
        
          subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
          body: '${FILE,path="myfile.html"}', 
          recipientProviders: [[$class: 'DevelopersRecipientProvider']],
       to: 'diksha2547@gmail.com'
     
        )
    }
  }
     
   
  
}
    
  
