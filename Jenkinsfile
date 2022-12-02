pipeline {
	agent none
        stages {
           stage ("tomcat buid & move to other node") {
	       agent {label "tom"}
              steps {
		      sh "echo ${BUILD_NUMBER}"
                      sh 'mvn deploy'
		      sh 'ls'
		      echo "sucessfully copied build to other node"
	      }
	   }
	   stage ('diploy in node2') {
	      agent {label "banglore"}
	   	steps {
		    sh 'curl -u neilp.cool@gmail.com:Devops123451! -O https://ebenneil.jfrog.io/artifactory/libs-release-local/com/efsavage/hello-world-war/${BUILD_NUMBER}/hello-world-war${BUILD_NUMBER}.war'
		    sh 'sudo cp -R hello-world-war-${BUILD_NUMBER}.war /opt/tomcat/webapps/'
		    sh 'sudo sh /opt/tomcat/bin/shutdown.sh'                   
                    sh 'sudo sleep 3'
                    sh 'sudo sh /opt/tomcat/bin/startup.sh'
                    echo "diployment is sucessfull"
                    echo "copy the public ip of instace and open it in browser with port:8090"
		}
	}
	} 	   
        }

