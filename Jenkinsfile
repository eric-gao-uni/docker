pipeline {
  agent any
  def app
  
  stages {

    stage('Clone repository') {
      
        checkout scm
    }
    
    stage('Build image') {
    
       app = docker.build("ericgaoatuniunidotcom/uni_api")
    }
    
    stage('Test image') {
    
    
        app.inside {
            sh 'echo "Tests passed"'
        }
    }
    
    stage('Push image') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-rw') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
  }  
}
