@Library("cred") _
pipeline {
    agent any
    environment{
        username= 'nikhilsonawane2jpg/jenkins'
        tag= '1.1'        
    }
    stages {
    

        stage('Checkout Code') {
            steps {
                echo 'Pulling code from GitHub'
            }
        }

        // stage('Build Docker Image') {
        //     steps {
        //         sh 'docker build -t $name .'
        //     }
        // }

        stage('build docker image'){
            steps{
                script{
                    shared($name, $tag)
                }
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
