pipeline {
    agent {label 'tom'}
    stages {
        stage ('My Build') { 
            steps {
              sh "echo ${BUILD_NUMBER}"
              sh 'mvn deploy'
              sh 'pwd'
              sh 'whoami'
            }
        }
        stage ('My deploy') { 
        agent {label 'banglore'}
            steps {
              sh 'pwd'
              sh 'whoami'
              sh 'curl -u neilp.cool@gmail.com:Devops123451! -O https://ebenneil.jfrog.io/artifactory/libs-release-local/com/efsavage/hello-world-war/${BUILD_NUMBER}/hello-world-war${BUILD_NUMBER}.war'
              sh 'sudo cp -R hello-world-war-${BUILD_NUMBER}.war /opt/tomcat/webapps/'
              sh 'sudo sh /opt/tomcat/bin/shutdown.sh'
              sh 'sleep 2'
              sh 'sudo sh /opt/tomcat/bin/startup.sh'
            }
        }
    }
}
