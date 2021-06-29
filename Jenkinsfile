pipeline {
  agent {
    docker {
      args '-p 3000:3000'
      image 'justthunder/emberfire-docker'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }

    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }

    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
      }
    }
  }

  post {
    always {
      echo 'Cleaning up workspace'
      deleteDir()
      }
    }  
}
