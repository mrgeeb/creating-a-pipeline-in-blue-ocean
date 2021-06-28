pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '#npm install'
        script {
          if (!(env.BRANCH_NAME).contains('jenkins') && !(env.BRANCH_NAME).startsWith('develop') && !(env.BRANCH_NAME).startsWith('staging/') && !(env.BRANCH_NAME).startsWith('release/') && !(env.BRANCH_NAME).startsWith('PR')){
            env.gitTag=env.BRANCH_NAME
          }
          env.AUTHOR_NAME=sh(script: "printf \$(git show -s --format='%an' HEAD)", returnStdout: true)
        }

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

  }
}