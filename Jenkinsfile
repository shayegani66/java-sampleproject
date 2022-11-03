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
          deploy adapters: [tomcat8(credentialsId: 'tomcat_user', path: '', url: 'http://ec2-54-82-233-179.compute-1.amazonaws.com:8080/manager/html/')], contextPath: '', onFailure: false, war: '**/*.war'
          
          
             post {
        always {
            junit skipPublishingChecks: true, testResults: '**/cpputest_*.xml'
        }
    }
        }
     
    
      }
    }
  }
}
