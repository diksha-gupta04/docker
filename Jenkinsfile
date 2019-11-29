node {
  def app
  stage('Clone repository') {
    checkout scm
  }
  
  stage('Build image') {
    app=docker.build("dock-image/latest")
  }
  
  stage('Test image') {
    app.inside {
      sh 'echo "Tests passed"
  }
  
  stage('Push Image') {
    docker.withRegistry('https://github.com/diksha-gupta04/docker.git', 'docker-hub-credentials') {
      app.push("${env.BUILD_NUMBER}")
      app.push("latest")
    }
  }
}
  
