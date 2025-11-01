pipeline {
  agent any

  environment {
    PORT = '3000'
  }

  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
  }
}
