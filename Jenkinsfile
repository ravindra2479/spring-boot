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
			        sudo docker build -t ravindra:latest .
	              
		        '''
	        }
	}
		stage ('Docker push') {
            steps {
		    
                docker.withRegistry('https://288357198731.dkr.ecr.us-east-1.amazonaws.com/ravindra', 'ecr:us-east-1:ECR-credentials') {
                docker.image('ravindra').push('latest')
	        
            }
	}
		}
}
}
