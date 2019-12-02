pipeline {
  agent any
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
  
