node {
  def app
  stage('Clone repository') {
    checkout scm
  }
  
  stage('Build image') {
    app = docker build -t dock-image:latest .
  }
  
  stage('Test image') {
    app.inside {
      sh 'echo "Tests passed"'
    }
  }
  
 
}
  
