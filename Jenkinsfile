pipeline {
  agent {
    dockerfile true
  }
    stages {
      stage('Clone repository') {
        steps {
        checkout scm
        }
      }
      
      stage('Build image') {
        steps {
        
        script {
            def customImage = docker.build("my-image:${env.BUILD_ID}")
          
          customImage.inside {
        sh 'make test'
          }
       }
      }
       }
      }
      }
    
  
