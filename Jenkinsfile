pipeline {
  agent {
        dockerfile {
            filename 'Dockerfile'
           
            args '-v /var/run/docker.sock:/var/run/docker.sock -u jenkins:docker'
        }
  }
    stages {
      stage('Clone repo') {
        checkout scm
      }
      
      stage('Build image') {
        steps {
          echo 'Starting to build docker image'
          
          script {
            def customImage = docker.build("my-image:${env.BUILD_ID}")
          }
        }
      }
    }
        
  }
  
