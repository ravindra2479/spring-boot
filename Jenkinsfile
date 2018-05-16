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
		 stage('Docker build')
        {
            steps
            {
                script
                {
			"sudo docker build -t boot-docker:${BUILD_NUMBER} ${WORKSPACE}"
                        "sudo docker run -p 8080:8080 boot-docker:${BUILD_NUMBER}"
                }
            }
        }
    }
}
