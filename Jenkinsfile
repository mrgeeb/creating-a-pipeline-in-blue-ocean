pipeline {
  agent any
  stages {
    stage('Workspace Preparation') {
      steps {
          sh 'git submodule update --init --recursive'
          script {
            env.gitTag=sh(script: "git tag --sort=committerdate | tail -1 || true", returnStdout: true).trim()
            env.AUTHOR_NAME=sh(script: "printf \$(git show -s --format='%an' HEAD)", returnStdout: true) 
          }
      }
    }
  } 
    
//     stage('Build') {
//       steps {
//         sh 'npm install'
//       }
//     }

//     stage('Test') {
//       environment {
//         CI = 'true'
//       }
//       steps {
//         sh './jenkins/scripts/test.sh'
//       }
//     }

//     stage('Deliver') {
//       steps {
//         sh './jenkins/scripts/deliver.sh'
//       }
//     }    
//   }
//   post {
//     always {
//       echo 'Cleaning up workspace'
//       deleteDir()
//       }
//   } 
 
}
