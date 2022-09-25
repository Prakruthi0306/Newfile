pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('jenkinsdocker')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/Prakruthi0306/Newfile.git'
			}
		}

		stage('Build') {

			steps {
				bat 'docker build -t prakruthi0306/dp-alpine:latest .'
			}
		}

		stage('Login') {

			steps {
				bat 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				bat 'docker push prakruthi0306/dp-alpine:latest'
			}
		}
	}

	post {
		always {
			bat 'docker logout'
		}
	}

}

