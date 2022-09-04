node {
  def tomcatWebApp = 'C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0\\webapps';
  def tomcatBin = 'C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0\\bin';
  def tomcatStatus = '';
  stage('SCM Checkout') {
      git branch: 'main', credentialsId: 'Github', url: 'https://github.com/AakashSawant/war-jenkins-practice.git'
  }
  stage('compile') {
      def mvnHome = tool name: 'Maven', type:'maven'
      bat "${mvnHome}/bin/mvn clean package" 
  }
  
  stage('deploy') {
    bat "copy target\\*.war  \"${tomcatWebApp}\\ROOT.war\"" 
  }
  
  stage('Start deployement') {
    sleep(time:5,unit: "SECONDS")
    bat "${tomcatBin}\\startup.bat"
    sleep(time:5,unit:"SECONDS")
    
  }

}
