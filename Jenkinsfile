pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/tohxuewang99/Lab_Practice'
            }
        }
        stage('Build') {
            steps {
                script {
                    // Use a Docker image for Composer
                    docker {
                        image 'composer:latest'
                    }
                    sh 'composer install'
                }
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
    }
    post {
        always {
            node {
                junit testResults: 'logs/unitreport.xml'
            }
        }
    }
}
