pipeline {
  agent none
  stages {
    stage('Print version') {
      parallel {
        stage('Run maven version') {
          agent {
            kubernetes {
              //cloud 'kubernetes'
              label 'maven'
              containerTemplate {
                name 'maven'
                image 'maven:3.3.9-jdk-8-alpine'
                ttyEnabled true
                command 'cat'
              }
            }
          }
          failFast true
          steps {
            container('maven') {
              sh 'mvn -version'
            }
          }
        }
        stage('Run node version') {
          agent {
            kubernetes {
              //cloud 'kubernetes'
              label 'node'
              containerTemplate {
                name 'node'
                image 'node:alpine'
                ttyEnabled true
                command 'cat'
              }
            }
          }
          failFast true
          steps {
            container('node') {
              sh 'node --version'
            }
          }
        }
      }
    }
  }
}
