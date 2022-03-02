pipeline {
  agent {
    node {
      label 'agent1'
    }

  }
  stages {
    stage('Clone') {
      steps {
        git(url: 'https://github.com/ialmit/devops-webapp.git', branch: 'master')
      }
    }

    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh '''whoami
date
echo $PATH
pwd
ls -la
./gradlew build --info'''
          }
        }

        stage('P1') {
          steps {
            sh '''date
echo run parallel!'''
          }
        }

        stage('P2') {
          steps {
            sh '''date 
echo Run Parallel!'''
          }
        }

      }
    }

    stage('publish') {
      steps {
        archiveArtifacts(artifacts: 'build/libs/*.war', fingerprint: true, onlyIfSuccessful: true)
      }
    }

  }
}