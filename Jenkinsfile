pipeline {
  agent {
        dockerfile {
            filename 'Dockerfile'
            additionalBuildArgs  '--build-arg JENKINSUID=`id -u jenkins` --build-arg JENKINSGID=`id -g jenkins` --build-arg DOCKERGID=`stat -c %g /var/run/docker.sock`'
            args '-v /var/run/docker.sock:/var/run/docker.sock -u jenkins:docker'
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
  
