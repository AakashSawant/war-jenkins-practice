pipeline {
  agent any
  tools {
    maven 'maven-3.6.3'
    tool name: 'JDK-8', type: 'jdk'
    jdk "jdk1.8.0_101"
  }
  stages {
    
    stage ('clone from Git') {
      steps {
        git branch: 'main', credentialsId: 'Github', url: 'https://github.com/AakashSawant/war-jenkins-practice.git'
      }
    }
    
    stage ('Build') {
      steps {
        sh 'mvn clean package'
        git branch: 'main', credentialsId: 'Github', url: 'https://github.com/AakashSawant/war-jenkins-practice.git'
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
