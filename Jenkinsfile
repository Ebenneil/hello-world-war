pipeline {
	agent none
        stages {
           stage ("Build") {
	       agent {label "tom"}
              steps {
                      sh 'sudo mvn package'
		      sh 'ls'
		      sh 'scp -R target/hello-world-war-1.0.0.war banglore@172.31.12.90:/opt/tomcat/webapps'
		      echo "sucessfully copied build to other node"
	      }
	   }
	   stage ('diploy') {
	      agent {label "banglore"}
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
