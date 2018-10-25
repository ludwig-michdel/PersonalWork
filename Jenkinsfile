pipeline {
  agent any
  stages {
    stage('Recuperation des sources') {
      steps {
        git(url: 'https://github.com/ludwig-michdel/PersonalWork.git', branch: 'master', credentialsId: 'loginGitHubLMI')
      }
    }
    stage('build maven') {
      steps {
        bat(script: 'Launch mvn install', encoding: 'UTF-8')
      }
    }
  }
}