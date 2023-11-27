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
          docker.withRegistry('https://registry.hub.docker.com','dockerhub_id'){
            app.push('${env.BUILD_NUMBER}')
          }
        }

      }
    }
  }
  environment {
    registry = 'amyslowski/lab'
  }
}
