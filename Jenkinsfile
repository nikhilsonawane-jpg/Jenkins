
pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                echo 'Pulling code from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins:1.0 .'
            }
        }

        stage('Verify Image') {
            steps {
                sh 'docker images | grep jenkins:1.0'
            }
        }
    }
}
