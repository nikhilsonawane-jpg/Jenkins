@Library("cred") _
pipeline {
    agent any
    environment{
        name= 'nikhilsonawane2jpg/jenkins:1.0'
        
    }
    stages {
        stage('hello'){
            steps{
                script{
                    hello()
                }
            }
        }

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
            withCredentials([usernamePassword(credentialsId: 'docker-cred', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh "echo '${DOCKER_PASS}' | docker login -u ${DOCKER_USER} --password-stdin"
                }
        }
        }


        stage('Push Docker Image') {
            steps {
                sh 'docker push $name'
            }
        }
}
    post{
        success{
            echo "done perfectly"
        }
        failure{
            echo "failureee"
        }
    }
}
