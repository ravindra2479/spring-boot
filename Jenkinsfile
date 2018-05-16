pipeline  {
	agent any
	tools {
		    maven 'maven3'
		    jdk 'Java8'
	    }

	stages {
		stage('init') {
			steps {
				    sh '''
				    	echo "PATH = ${PATH}"
				    	echo "M2_HOME = ${M2_HOME}"
				    '''
			    }
		}
        stage ('Build') {
			steps {
				sh 'mvn install'
			}
		}
		
	stage ('Docker build') {
    	    steps {
		        sh '''
			        sudo docker build -t demo
	              
		        '''
	        }
	}
		stage ('Docker push') {
            steps {
                sudo docker.withRegistry('https://288357198731.dkr.ecr.us-east-1.amazonaws.com/ravindra:latest', 'ecr:us-east-1:ECR-credentials') {
                sudo docker.push('demo').image('latest')
            }
	}
		}
}
}
