pipeline {
	agent any

	stages {
  	  stage('Unit Tests') {
		steps {
		  sh 'ant -f test.xml -v'
		  junit 'reports/result.xml' 
		  sh 'aws --version'	
		}
	  }
  	  stage('Build') {
		steps {
	          sh 'ant -f build.xml -v'
		}
	  }	
  	  stage('Deploy') {
		steps {
			sh 'aws s3 cp ${WORKSPACE}/${JOB_NMAE}/dist/rectangle-${BUILD_NUMBER}.jar s3://lesherd-assignment-9/rectangle-${BUILD_NUMBER}.jar'			
		}
	  }		
	}
}
