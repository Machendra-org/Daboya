pipeline {
  agent any
  
  stages {
    stage ('Git clone') {
      steps{
        git branch: 'main', url:'https://github.com/Aatmaani-org/Production.git'
      }
    }

   stage ('Create Image') {
     steps{
       sh 'docker build -t Daboya-app .'
     }
  }
  
  stage ('Push image to ECR and Creating pod using Helm') {
      steps{
        sh ''' 
          docker tag Daboya-app:latest 883195043912.dkr.ecr.us-west-2.amazonaws.com/Daboya-repository-dev
          docker tag Daboya-app:latest 883195043912.dkr.ecr.us-west-2.amazonaws.com/Daboya-repository-dev:dev-latest
          aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin 883195043912.dkr.ecr.us-west-2.amazonaws.com
          docker push 883195043912.dkr.ecr.us-west-2.amazonaws.com/Daboya-repository-dev
          docker push 883195043912.dkr.ecr.us-west-2.amazonaws.com/Daboya-repository-dev:dev-latest
        '''
     }
    }

