node {
  def app
  stage('Clone repository') {
    checkout scm
  }
  stage('Build image') {
    app = docker.build("flepceska/jenkins_ex")
  }
  stage('Push image') {   
    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
      app.push("dev-${env.BUILD_NUMBER}")
      app.push("dev-latest")
      // signal the orchestrator that there is a new version
    }
  }
}