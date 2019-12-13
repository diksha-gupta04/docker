def status1 = 'FAILURE'
def status2 = 'FAILURE'
pipeline {
 environment {
    registry = "dikshagupta04/docker-test"
    registryCredential = 'dockerhub'
  }
 
  agent any
 
    stages {
        stage('Cloning Git') {
         steps{
          echo "Cloning Git"
          script {
           try {
            git 'https://github.com/diksha-gupta04/docker.git'
          status1 = 'SUCCESS'
          echo "Cloning done!"
           }
           catch(Exception e) {
            status1 = 'FAILURE' 
         }
        
          }
         }
         }
         
      stage('Building image') {
      steps{
        echo "Building image"
        script {
         try {
          def customImage = docker.build("my-image:${env.BUILD_ID}")
          status2 = 'SUCCESS'
          echo "Build the image!!"
        }
         catch(Exception e) {
            status2 = 'FAILURE' 
         }
         
        
      }
      }
     
      }
    }
    
    post {
     
      failure {
       echo "Build Failure!!"
         emailext (
            attachLog: true,
            subject: "${currentBuild.currentResult}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
            body: """<p>EXECUTED: Job <b>\'${env.JOB_NAME}:${env.BUILD_NUMBER}\'
                </b></p><p>View console output at "<a href="${env.BUILD_URL}">${env.JOB_NAME}:${env.BUILD_NUMBER}</a>"</p> 
                <p><i>(Build log is attached.)</i></p> \n
                <p>"stage 1: ${status1}"</p>\n
                <p>"stage 2(Building image): ${status2}"</p> """,
            
            to: 'diksha2547@gmail.com'
       
        )
    }
     
      success {
        echo "Build Success!!"
         emailext (
            attachLog: true,
            subject: "${currentBuild.currentResult}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
            body: """<p>EXECUTED: Job <b>\'${env.JOB_NAME}:${env.BUILD_NUMBER}\'
                </b></p><p>View console output at "<a href="${env.BUILD_URL}">${env.JOB_NAME}:${env.BUILD_NUMBER}</a>"</p> 
                <p><i>(Build log is attached.)</i></p>  \n
                <p>"stage 1(Cloning Git): ${status1}"</p> \n
                <p>"stage 2(Building image): ${status2}"</p>""",
            
            to: 'diksha2547@gmail.com'
       
        )
    }

   
    }
     
   
  
}
    
  
