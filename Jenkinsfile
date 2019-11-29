node {
  def app
  
  stage('Clone repository') {
    checkout scm
  }
  
  stage('Build Image') {
    app = docker.build("dockimage/latest")
  }
}
