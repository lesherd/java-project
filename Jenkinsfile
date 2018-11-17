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
			sh 'aws s3 cp ${WORKSPACE}/${JOB_NMAE}/dist/rectangle-${BUILD_NUMBER}.jar s3://lesherd-assignment-9/rectangle-${BUILD_NUMBER}.jar'			
		}
	  }
	  stage('Report') {
		  steps {
                       withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'jenkins-aws', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                         sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'  
                       }			  
		  }	  
	  }
	}  
}
