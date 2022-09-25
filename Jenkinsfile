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
				sh 'docker build -t prakruthi0306/dp-alpine:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push prakruthi0306/dp-alpine:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}

