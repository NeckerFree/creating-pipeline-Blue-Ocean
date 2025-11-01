pipeline {
  agent {
    docker {
      image 'node:18-alpine'
      args '-p 3000:3000'
    }
  }

  environment {
    PORT = '3000'
  }

  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM',
          branches: [[name: '*/main']],
          userRemoteConfigs: [[
            url: 'https://github.com/NeckerFree/creating-pipeline-blue-ocean.git',
            credentialsId: 'github-token'
          ]]
        ])
      }
    }

    stage('Install') {
      steps {
        sh 'npm install'
      }
    }

    stage('Build') {
      steps {
        sh 'npm run build || echo "No build script found"'
      }
    }
  }

  post {
    success {
      echo "✅ Build completed successfully!"
    }
    failure {
      echo "❌ Build failed!"
    }
  }
}
