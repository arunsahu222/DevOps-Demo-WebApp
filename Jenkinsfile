pipeline {
  agent any
  
  tools {
    maven "maven latest"
    java 'jdk8'
  }
  stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
               slackSend channel: "#case-study-alerts", message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}"
         
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 

       
      }
    }
        }
    stage('Deploy') {
      steps {
        echo 'Deployed'
      }
    }

  }

