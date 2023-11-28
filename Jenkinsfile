pipeline {
  agent any
  stages {
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
