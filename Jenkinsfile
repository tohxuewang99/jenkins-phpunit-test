pipeline {
	agent any
	stages {

		stage('Test') {
			steps {
                sh '/var/jenkins_home/.composer/vendor/bin/phpunit --logs-junit logs/unitreport.xml -c tests/phpunit.xml tests'
            }
		}
	}
	post {
	    always {
	        junit testResults: 'logs/unitreport.xml'
	    }
	}
}
