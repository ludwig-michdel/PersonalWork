pipeline {
  agent any
  stages {
    stage('Recuperation des sources') {
      steps {
        git(url: 'https://github.com/ludwig-michdel/PersonalWork.git', branch: 'master', credentialsId: 'loginGitHubLMI')
      }
    }
    stage('error') {
      steps {
        mail(subject: '[AL 32 - JpetStore] Build', body: 'Bonjour, un nouveau build s\'est correctement déroulé grâce à BlueOcean ! Vers l\'infini et Yallah !', from: 'ludovic.michaudel@gmail.com', to: 'ludovic.michaudel@gmail.com', charset: 'UTF-8', cc: 'kvin.ly@gmail.com')
      }
    }
    stage('build maven') {
      steps {
        bat(script: 'Launch mvn install', encoding: 'UTF-8')
      }
    }
  }
}