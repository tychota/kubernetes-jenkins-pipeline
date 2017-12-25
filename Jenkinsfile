pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            sh 'echo "Hello World"'
            sh '''
                    echo "Multiline shell steps"
                    ls -lah
                '''
          }
        }
        stage('git status') {
          steps {
            sh 'git status'
          }
        }
      }
    }
    stage('Blop 2') {
      steps {
        input(message: 'Destroy the world', ok: 'Yes', submitter: 'blop', submitterParameter: 'blop')
      }
    }
  }
}