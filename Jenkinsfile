pipeline {
	agent {
		docker {
			image 'php:8.2'
		}
	}
	stages {
		stage('Build') {
			steps {
				sh 'composer install'
			}
		}
		stage('Test') {
			steps {
                sh './vendor/bin/phpunit --logs-junit logs/unitreport.xml -c tests/phpunit.xml tests'
            }
		}
	}
	post {
	    always {
	        junit testResults: 'logs/unitreport.xml'
	    }
	}
}
