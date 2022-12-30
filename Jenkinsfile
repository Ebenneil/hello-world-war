pipeline {
	agent none
        stages {
           stage ("Build") {
	       agent {label "slave"}
              steps {
                      sh 'sudo mvn package'
		      sh 'ls'
		      sh 'scp -R target/hello-world-war-1.0.0.war build@172.31.34.237:/opt/tomcat/webapps/'
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
