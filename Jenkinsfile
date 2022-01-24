pipeline {
  agent any
  tools {
    maven 'Maven' 
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat8(credentialsId: 'tomcat_user', path: '', url: 'http://ec2-http://ec2-18-209-87-198:8080/.compute-1.amazonaws.com:8080')], contextPath: '', onFailure: false, war: '**/*.war' 
        }
      }
    }
  }
}
