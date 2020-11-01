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
            steps { 
              rtServer (
    id: 'artifactory',
    url: 'https://arunsahu2222.jfrog.io/artifactory',
    // If you're using username and password:
    username: 'deploy1',
    password: '10@Storage'

            )
            }
   }
//}
      stage ('Upload file') {
            steps {
                rtUpload (
                    serverId: 'artifactory',
                    spec: """{
                            "files": [
                                    {
                                        "pattern": "*.war",
                                        "target": "deploy1"
                                    }
                                ]
                            }"""
                )
               rtMavenDeployer (
                    id: "MAVEN_DEPLOYER",
                    serverId: 'artifactory',
                    releaseRepo: "deploy1",
                    snapshotRepo: "deploy1"
                )

                rtMavenResolver (
                    id: "MAVEN_RESOLVER",
                    serverId: 'artifactory',
                    releaseRepo: "deploy1",
                    snapshotRepo: "deploy1"
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


