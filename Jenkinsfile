pipeline {
  agent any
  
  tools {
    maven "maven latest"
  }
  stages {
    stage('Commit change') {
      steps {
        
        echo 'Build Successful'
      }
    }

    stage('Clone source') {
      steps {
        git url: 'https://github.com/tipurmadan/DevOps-Demo-WebApp.git'
        echo 'source cloned'
      }
    }
    
    stage('Build') {
      steps {
        // get code from git repo
        git 'https://github.com/tipurmadan/DevOps-Demo-WebApp.git'
        
        
        sh "mvn clean compile"
        slackSend channel: "#case-study-alerts", message: "Build Started: ${env.JOB_NAME} ${env.BUILD_NUMBER}"
        echo 'Build Success'
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deployed'
      }
    }

  }
}
