pipeline {
  environment {
    registry = "arunsahu222/dockercasestudy"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
 
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  //  stage('Remove Unused docker image') {
   //   steps{
  //      sh "docker rmi $registry:$BUILD_NUMBER"
  //    }
   // }
  }
}
