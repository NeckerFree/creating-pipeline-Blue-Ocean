pipeline {
  agent {
    docker {
      image 'node:18-alpine'
      args 'PORT=3000'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }

  }
}