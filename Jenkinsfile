pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '''-v /var/run/docker.sock:/var/run/docker.sock -p 3000:3000'''
    }
  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      steps {
        sh 'echo "Tests would run here"'
      }
    }
  }
}
