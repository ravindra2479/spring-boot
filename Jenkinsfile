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
			"sudo docker build -t "docker:01" /var/lib/jenkins/workspace/PIPELINE/"
                        
                }
            }
        }
    }
}
