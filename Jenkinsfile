pipeline {
  agent any
  
  triggers {
        pollSCM 'H/2 * * * *'
    }
  
  tools {
    maven "maven latest"
  }
 
  
  stages{
    
   
    
 //   stage('Sonarqube') {
  //  environment {
  //      scannerHome = tool 'sonarqubescanner'
 //   }
 //   steps {
 //       withSonarQubeEnv('sonarqube') {
        //     sh 'mvn clean package sonar:sonar'
  //        sh 'mvn clean package sonar:sonar -Dsonar.sources=. -Dsonar.tests=. -Dsonar.test.inclusions=**/test/java/servlet/createpage_junit.java -Dsonar.exclusions=**/test/java/servlet/createpage_junit.java -Dsonar.login=admin -Dsonar.password=admin'
//        }
//    }
   stage ('Server config') {
            steps { rtServer (
    id: 'Artifactory-1',
    url: 'https://arunsahu2222.jfrog.io/artifactory',
    // If you're using username and password:
    username: 'deploy1',
    password: '10@Storage'
    
    // The default value (if not configured) is 300 seconds:
    timeout = 300
            )}}
//}
      stage ('Upload file') {
            steps {
                rtUpload (
                    serverId: 'Artifactory-1',
                    spec: """{
                            "files": [
                                    {
                                        "pattern": "*.war",
                                        "target": "deploy1"
                                    }
                                ]
                            }"""
                )
            }
        }

        stage ('Publish build info') {
            steps {
                rtPublishBuildInfo (
                    serverId: artifactory
                )
            }
        }
    
    stage('Deploy') {
      steps {
        echo 'Deployed'
      }
    }

  }
}


