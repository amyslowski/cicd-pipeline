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
        sh '''chmod 744 scripts/build.sh
scripts/build.sh'''
      }
    }

    stage('test') {
      steps {
        sh 'scripts/test.sh'
      }
    }

    stage('docker build') {
      steps {
        sh 'docker build -t appnjs .'
      }
    }

  }
  environment {
    registry = 'amyslowski/lab'
  }
}