pipeline {
  agent {label 'tom'}
  stages {
    stage ('my build') {
      steps {
        sh 'mvn package'    
      }
    }
stage ('my deploy') {
   agent {label 'banglore'}
   steps {
        sh 'sudo scp -R /declarative pipeline/target/hello-world-war-1.0.0.war /opt/tomcat/webapps/'
        sh 'sudo sh /opt/tomcat/bin/shutdown.sh'
        sh 'sleep 2'
        sh 'sudo sh /opt/tomcat/bin/startup.sh'
      }
    }
  }
}
