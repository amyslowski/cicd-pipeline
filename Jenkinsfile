pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        git(url: 'https://github.com/amyslowski/cicd-pipeline', branch: 'master', credentialsId: 'github_ID')
      }
    }

  }
}