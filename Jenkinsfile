pipeline {
  agent none
  stages {
    stage ('Build') {
      agent { label 'tom' }
      steps {
        sh "echo ${BUILD_NUMBER}"
        sh 'mvn deploy'
        sh 'pwd'
      }
    }
    stage ('Deploy') {
      agent { label 'banglore' }
      steps {
        sh 'pwd'
        sh 'whoami'
        sh 'curl -u neilp.cool@gmail.com:Devops123451! -O https://ebenneil.jfrog.io/artifactory/libs-release-local/com/efsavage/hello-world-war/${BUILD_NUMBER}/hello-world-war${BUILD_NUMBER}.war'
        sh 'sudo cp -R hello-world-war-${BUILD_NUMBER}.war /opt/tomcat/webapps'
        sh 'sudo sh /opt/apache-tomcat-10.0.27/bin/shutdown.sh'
        sh 'sleep 3'
        sh 'sudo sh /opt/apache-tomcat-10.0.27/bin/startup.sh'
      }
    }
  }
}

