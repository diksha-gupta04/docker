pipeline {
  agent {
        dockerfile {
            filename 'Dockerfile'
           
            args '-v /var/run/docker.sock:/var/run/docker.sock -u jenkins:docker'
        }
  }
    stages {
      stage('Clone repository') {
        checkout scm
      }
      
      stage('Build image') {
        script {
            def customImage = docker.build("my-image:${env.BUILD_ID}")
       }
      }
    }
        
  }
  
