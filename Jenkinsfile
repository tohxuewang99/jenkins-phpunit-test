pipeline {
	agent {
		docker {
			image 'composer:latest'
		}
	}
	stage('Test') {
            steps {
                script {
                    // Use a Docker image that contains PHP and PHPUnit
                    docker {
                        image 'php:latest'
                    }
                    sh './vendor/bin/phpunit --log-junit logs/unitreport.xml -c tests/phpunit.xml tests'
                }
            }
        }
	post {
	    always {
	        junit testResults: 'logs/unitreport.xml'
	    }
	}
}
