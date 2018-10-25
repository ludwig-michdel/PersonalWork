pipeline {
  agent any
  stages {
    stage('Récupération des sources') {
      steps {
        git(url: 'https://github.com/ludwig-michdel/PersonalWork.git', branch: 'master', credentialsId: 'loginGitHubLMI')
      }
    }
    stage('') {
      steps {
        mail(subject: '[AL 32 - JpetStore ] Build', body: 'Bonjour, un nouveau build s\'est correctement déroulé grâce à BlueOcean ! Vers l\'infini et Yallah !', from: '[admin jpetstore]', to: 'ludovic.michaudel@gmail.com', charset: 'UTF-8', cc: 'kvin.ly@gmail.com')
      }
    }
  }
}