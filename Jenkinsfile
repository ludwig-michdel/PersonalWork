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
        withSonarQubeEnv('sonar') {
          bat(script: 'runsonar.bat', encoding: 'UTF-8', returnStatus: true)
        }

      }
    }

	stage('quality gate') {
		steps {
		
			withSonarQubeEnv('sonar') {
				timeout(time:10, unit: 'MINUTES') {
					waitForQualityGate(abortPipeline: true)
				}
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