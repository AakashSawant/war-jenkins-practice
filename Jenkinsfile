pipeline {
  agent any
  tools {
    maven 'maven-3.6.3'
    jdk "jdk1.8.0_101"
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'Tomcat', path: '', url: 'http://localhost:8081')], contextPath: null, war: '**/*.war'
        }
      }
    }
  }
}
