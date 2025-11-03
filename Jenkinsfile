pipeline {
    agent {
        docker {
            image 'node:20-alpine'
            args '--privileged -v /var/run/docker.sock:/var/run/docker.sock'
        }
    }
    environment {
        // Use your GitHub credential ID here
        GIT_CREDENTIALS = 'github-elio'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [],
                    userRemoteConfigs: [[
                        url: 'https://github.com/NeckerFree/creating-pipeline-blue-ocean.git',
                        credentialsId: "${GIT_CREDENTIALS}"
                    ]]
                ])
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Build') {
            steps {
                sh 'npm run build'  // optional, if your project has a build script
            }
        }
    }
}
