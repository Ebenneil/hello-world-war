pipeline {
	agent {label 'tom'}
       stages {
           stage ('Build') {
              steps {
                 sh 'mvn package'
                 sh 'pwd'
                 sh 'whoami'
                 sh 'scp -R /home/tom/workplace/declarative_pipeline/target/hello-world-war-1.0.0.war server@172.31.12.90:/opt/tomcat/webapps'
                }
           }
           stage ('deploy') {
           agent {label 'banglore'}
               steps {
                  sh 'pwd'
                  sh 'sudo sh /opt/tomcat/bin/shutdown.sh'
                  sh 'sleep 2'
                  sh 'sudo sh /opt/tomcat/bin/startup.sh'
                 }
               }
           }
       }
