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
          deploy adapters: [tomcat8(credentialsId: 'tomcat-user', path: '', url: 'http://ec2-3-85-102-189.compute-1.amazonaws.com:8080/manager/html/')], contextPath: '', onFailure: false, war: '**/*.war' 
        }
      }
    }
  }
}
