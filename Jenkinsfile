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
       archiveArtifacts artifacts: 'generatedFile.txt'
       echo 'I will always say Hello!'
          emailext attachLog: true,
           attachmentsPattern: 'generatedFile.txt',
       body: "${currentBuild.result}: Job ${env.JOB_NAME}- build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
        recipientProviders: [[$class: 'DevelopersRecipientProvider'] , 
                             [$class: 'RequestorRecipientProvider']],
        subject: "Jenkins Build: ${currentBuild.result}: Job ${env.JOB_NAME}",
       to: 'diksha2547@gmail.com'
        }
     }
     
   
  
}
    
  
