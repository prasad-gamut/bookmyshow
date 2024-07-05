pipeline {
    agent any

//	tools {
//		jdk 'jdk8'
//	}
//	environment {
//		M2_INSTALL = "/usr/bin/mvn"
//	}

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	checkout scm
	    	}
        }

        stage('Build') {
            steps {
                sh 'mvn install -Dmaven.test.skip=true'
            }
        }
		
        stage('Unit Tests') {
            steps {
                sh 'mvn compiler:testCompile'
                sh 'mvn surefire:test'
            }
        }

        stage('Deployment') {
            steps {
                sh 'scp /.jenkins/workspace/sonix/target/flipkart-1.0-SNAPSHOT.jar root@ip-172-31-34-207:/test_env/test-server/webapps'
                
            }
        }
    }
}
