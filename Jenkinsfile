
pipeline {
    agent any
    environment{
        name: 'nikhilsonawane-jpg/jenkins:1.0'
        
    }
    stages {

        stage('Checkout Code') {
            steps {
                echo 'Pulling code from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $name .'
            }
        }
        stage('Docker login'){
        steps {
            withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh 'docker login -u $DOCKER_USER -p $DOCKER_PASS'
                }
        }
        }


        stage('Push Docker Image') {
            steps {
                sh 'docker push $name'
            }
        }
    }
}
