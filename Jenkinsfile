pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        script {
          checkout scm
          def customImage = docker.build("${registry}:${env.BUILD_ID}")
        }

      }
    }

    stage('test') {
      steps {
        script {
          docker.image("${registry}:${env.BUILD_ID}").inside{
            c-> sh './scripts/test.sh'}
          }

        }
      }

    }
    environment {
      registry = 'amyslowski/lab'
    }
  }