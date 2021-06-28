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
        sh 'apk add git'
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