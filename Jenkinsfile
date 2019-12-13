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
     
      always {
      
      emailext (
       
         subject: "${currentBuild.currentResult}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
          body: """<p>EXECUTED: Job <b>\'${env.JOB_NAME}:${env.BUILD_NUMBER})\'
   </b></p><p>View console output at "<a href="${env.BUILD_URL}"> 
   ${env.JOB_NAME}:${env.BUILD_NUMBER}</a>"</p> 
     <p><i>(Build log is attached.)</i></p> """
          recipientProviders: [[$class: 'DevelopersRecipientProvider']],
       to: 'diksha2547@gmail.com'
       
        )
    }

   
    }
     
   
  
}
    
  
