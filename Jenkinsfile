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
        sh "docker build -t ${registry}:${env.BUILD_NUMBER} ."
      }
    }

    stage('Publish') {
      steps {
        sh '"docker login -u amyslowski -p ${dockerhub_secret}"'
        sh "docker push ${registry}:${BUILD_NUMBER}"
      }
    }

  }
  environment {
    registry = 'amyslowski/lab'
  }
}