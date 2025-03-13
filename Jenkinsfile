pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/aryanvaychal/PES2UG22CS105_Jenkins.git']],
                    extensions: [[$class: 'CleanCheckout']] // Clean clone
                ])
            }
        }

        stage('Debug') {
            steps {
                sh 'ls -la'
                sh 'pwd'
            }
        }

        stage('Build') {
            steps {
                sh 'cd $WORKSPACE && g++ hello.cpp -o output'
            }
        }

        stage('Test') {
            steps {
                sh './output'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
