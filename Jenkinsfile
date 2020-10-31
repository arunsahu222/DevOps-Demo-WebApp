pipeline {
  agent any
  
  triggers {
        pollSCM 'H/2 * * * *'
    }
  
  tools {
    maven "maven latest"
  }
 
  
  stages{
    
   
    
    stage('Sonarqube') {
    environment {
        scannerHome = tool 'sonarqubescanner'
    }
    steps {
        withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
        }
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }
    }
}
    
    stage('Deploy') {
      steps {
        echo 'Deployed'
      }
    }

  }
}


