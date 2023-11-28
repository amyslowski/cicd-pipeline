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
        script {
          docker.withRegistry('','dockerhub_id'){
          docker.image("${registry}:${env.BUILD_NUMBER}").push()
          }
      }
    }
    }
  }
  environment {
    registry = 'amyslowski/lab'
  }
}
