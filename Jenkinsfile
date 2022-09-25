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
        git '
