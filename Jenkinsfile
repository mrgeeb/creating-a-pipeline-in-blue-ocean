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

    stage('error') {
      steps {
        sh '''#/usr/bin/env bash
echo "Unit Test from UAT"
              










'''
      }
    }

  }
  post {
    always {
      echo 'Cleaning up workspace'
      deleteDir()
      script{
        def cred="slack-secret4.0"
        def teamDomain="diamunfikri"
        def channel="secretproject-40"
        slackSend channel: "${channel}", failOnError: true, color: "good", message: "*${currentBuild.currentResult}:*\n build no.${env.BUILD_NUMBER}", teamDomain: "${teamDomain}", tokenCredentialId: "${cred}"
      }
    }

  }
}
