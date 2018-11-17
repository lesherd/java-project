pipeline {
	agent any

	stages {
  	  stage('Unit Tests') {
		steps {
		  git url: 'https://github.com/lesherd/java-project.git', branch: 'master'	
	          sh 'ant -f test.xml -v'
		  junit 'reports/result.xml'   	
		}
	  }
  	  stage('Build') {
		steps {
	          sh 'ant -f build.xml -v'
		}
	  }		
	}
}
