pipeline {
	agent any
	
	tools {
		maven 'maven3'
		jdk 'Java8'
	}
	
	stages {
		stage('Init') {
			steps {
				sh '''
					echo "PATH = ${PATH}"
					echo "M2_HOME = ${M2_HOME}"
				'''
			}
		}
		
		stage('Build') {
			steps {
				sh 'mvn install'
			}
		}
		stage ('Docker build') {
    	    steps {
		        sh '''
			        sudo docker build -t demo
	                sudo docker run -p 8081:8585 demo
		        '''
	        }
	}
		stage ('Docker push') {
            steps {
		    sh '''
                docker.withRegistry('https://288357198731.dkr.ecr.us-east-1.amazonaws.com/ravindra', 'ecr:us-east-1:ECR-credentials') {
                docker.image('demo').push('latest')
		'''
            }
	}
		}
    }
}
