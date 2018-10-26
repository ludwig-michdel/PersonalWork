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
        bat(script: 'runmaven.bat', encoding: 'UTF-8')
      }
    }
    stage('qualimetrie') {
      steps {
        withSonarQubeEnv('JPetStore Demo 6') {
          bat(script: 'runsonar.bat', encoding: 'UTF-8', returnStatus: true)
          waitForQualityGate(abortPipeline: true)
        }

      }
    }
    stage('publication') {
      steps {
        nexusArtifactUploader(artifacts: [
                                                  					[artifactId: 'jpetstore', classifier: 'debug', file: 'target/jpetstore.war', type: 'war']
                                                  				], nexusVersion: 'nexus3', protocol: 'http', nexusUrl: 'localhost:8081', groupId: 'jpetstore', version: '1.1-SNAPSHOT', repository: 'maven-snapshots', credentialsId: 'adminNexus')
        }
      }
    }
  }