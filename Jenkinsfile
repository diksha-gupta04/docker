node {
  def app
  
  stage('Clone repository') {
    chcekout scm
  }
  
  stage('Build Image') {
    app = docker.build("dockimage/latest")
  }
}
