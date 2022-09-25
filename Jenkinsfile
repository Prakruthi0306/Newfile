pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('DockerCredentials')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/Prakruthi0306/Newfile.git'
            }
        }

        stage('Build docker image') {
            steps {  
                bat 'docker build .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push valaxy/nodeapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}

