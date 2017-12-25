pipeline {
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
  stages {
    stage('Run maven') {
      steps {
        container('maven') {
          sh 'mvn -version'
        }
      }
    }
  }
  stage('Run node') {
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
      steps {
        container('node') {
          sh 'node -version'
        }
      }
    }
  }
}
