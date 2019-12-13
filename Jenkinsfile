def status1 = 'FAILURE'
def status2 = 'FAILURE'
def stageName = ' '
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
           stageName = 'Cloning Git'
           try {
            git 'https://github.com/diksha-gupta04/docker.git'
            status1 = ${stageName}+': SUCCESS'
          echo "Cloning done!"
           }
           catch(Exception e) {
            status1 = ${stageName}+': FAILURE' 
         }
        
          }
         }
         }
         
      stage('Building image') {
       
      steps{
        echo "Building image"
       
        script {
         stageName = 'Building image'
         try {
          def customImage = docker.build("my-image:${env.BUILD_ID}")
          status2 = ${stageName}+': SUCCESS'
          echo "Build the image!!"
        }
         catch(Exception e) {
            status2 = ${stageName}+': FAILURE'
         
        
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
                <p>${status1}</p>\n
                <p>${status2}</p> """,
            
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
                <p>${status1}</p> \n
                <p>${status2}</p>""",
            
            to: 'diksha2547@gmail.com'
       
        )
    }
    }
}
    
  
