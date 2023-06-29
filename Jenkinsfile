pipeline {
	agent any
	tools {
        maven 'm1' 
    }
	stages {
		stage ('build') {
			steps {
				sh 'mvn clean install'
			}
		
		}
		stage ('test') {
			steps {
				sh 'mvn test'
			}
			post {
				always {
					junit 'target/surefire-reports/*.*xml'
				}
			}
		}
		stage ('run') {
			steps {
				sh './scripts/deliver.sh'
			}
		
		}
	}
}
