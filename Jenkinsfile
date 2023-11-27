pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        script {
          checkout scm
        }

      }
    }

    stage('build') {
      steps {
        sh './scripts/build.sh'
      }
    }

  }
  environment {
    registry = 'amyslowski/lab'
  }
}