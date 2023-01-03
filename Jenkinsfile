pipeline {
	agent none
        stages {
           stage ("Build") {
	       agent {label "slave"}
              steps {
		      sh "echo ${BUILD_NUMBER}"
                      sh 'sudo mvn package'
		      sh 'ls'
		      sh 'scp -R /home/slave/workspace/job1/target/hello-world-war-null.war build@172.31.34.237:/opt/tomcat/webapps/'
		      echo "sucessfully copied build to other node"
		      sh 'pwd'
	      }
	   }
	   stage ('deploy') {
	      agent {label "slavebuild"}
	   	steps {
		    sh 'sudo sh /opt/tomcat/bin/shutdown.sh'                   
                    sh 'sudo sleep 3'
                    sh 'sudo sh /opt/tomcat/bin/startup.sh'
                    echo "diployment is sucessfull"
                    echo "copy the public ip of instace and open it in browser with port:8090"
		}
	     }
	  } 	    
       }
pipeline {
    agent {label 'slave'}
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
        agent {label 'slavebuild'}
            steps {
              sh 'pwd'
              sh 'whoami'
              sh 'curl -u neilp.cool@gmail.com:Neil886778353831! -O https://neilpinto.jfrog.io/artifactory/libs-release-local/com/efsavage/hello-world-war/${BUILD_NUMBER}/hello-world-war-${BUILD_NUMBER}.war'
              sh 'sudo cp -R hello-world-war-${BUILD_NUMBER}.war /opt/tomcat/webapps/'
              sh 'sudo sh /opt/tomcat/bin/shutdown.sh'
              sh 'sleep 2'
              sh 'sudo sh /opt/tomcat/bin/startup.sh'
            }
        }
    }
}
