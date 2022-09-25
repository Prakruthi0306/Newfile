pipeline{
  environment{
    registry="prakruthi0306/mkdocs"
    registryCredentials= 'DockerCredentials'
    dockerImage= ''
  }
  agent any 
  stages {
    stage ('Cloning Git'){
      steps {
        git 'https://github.com/Prakruthi0306/Newfile.git'
      }
    }
    stage('Build image'){
      steps{
        script{
          dockerImage = docker.build registry + ":BUILD_NUMBER"
        }
      }
    }
    stage('Deploy image') {
      steps{
        script{
          docker.withRegistry('',registryCredentials ){
            dockerImage.push()
          }
        }
      }
    }
  }
}
