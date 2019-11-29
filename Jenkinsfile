pipeline {
  
  environment {
    registry = diksha-gupta04/docker
    registryCredentials = 'github'
  }
  agent any
  stages {
  
  
  stage('Build image') {
    steps {
      script {
        docker.build regsirty + ":BUILD_NUMBER"
      }}}
  
  
  }
}
  
