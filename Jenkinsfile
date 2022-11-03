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
    
    publishChecks name: 'example', title: 'Pipeline Check', summary: 'check through pipeline',
    text: 'you can publish checks in pipeline script',
    detailsURL: 'https://github.com/jenkinsci/checks-api-plugin#pipeline-usage',
    actions: [[label:'an-user-request-action', description:'actions allow users to request pre-defined behaviours', identifier:'an unique identifier']]
    
    
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat8(credentialsId: 'tomcat-user', path: '', url: 'http://ec2-54-82-233-179.compute-1.amazonaws.com:8080/manager/html/')], contextPath: '', onFailure: false, war: '**/*.war' 
        }
      }
    }
  }
}
