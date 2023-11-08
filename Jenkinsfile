pipeline {
	agent any

	environment {
		PHP_VERSION = '8.2' // Change this to the desired PHP version
	}

	stages {
		stage('Install PHP') {
			steps {
				script {
					// Install PHP on the Jenkins machine
					sh "apt-get update && apt-get install -y php$PHP_VERSION php$PHP_VERSION-cli php$PHP_VERSION-mbstring"
				}
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
