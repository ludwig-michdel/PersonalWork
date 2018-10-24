pipeline {
  agent any
  stages {
    stage('prepare') {
      steps {
        sleep(time: 10, unit: 'MINUTES')
      }
    }
    stage('build') {
      steps {
        echo 'coucou'
        sh 'mvn'
      }
    }
  }
}