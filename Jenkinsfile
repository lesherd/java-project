pipeline {
	agent any

	stages {
  	  stage('Unit Tests') {
		steps {
	          sh 'ant -f test.xml -v'
		  junit 'reports/result.xml'   	
		}
	  }
  	  stage('Build') {
		steps {
	          sh 'ant -f build.xml -v'
		}
	  }	
  	  stage('Deploy') {
		steps {
		  sh '/usr/local/bin/aws --version'
                  sh '/usr/local/bin/aws s3 cp rectangle-${BUILD_NUMBER}.jar s3://lesherd-assignment-9/rectangle-${BUILD_NUMBER}.jar'			
		}
	  }		
	}
}
