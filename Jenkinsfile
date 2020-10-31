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
        //     sh 'mvn clean package sonar:sonar'
          sh 'mvn clean package sonar:sonar -Dsonar.sources=. -Dsonar.tests=. -Dsonar.test.inclusions=**/test/java/servlet/createpage_junit.java -Dsonar.exclusions=**/test/java/servlet/createpage_junit.java -Dsonar.login=admin -Dsonar.password=admin'
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


