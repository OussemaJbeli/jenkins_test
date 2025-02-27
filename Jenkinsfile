pipeline {
    agent any

    environment {
        GIT_USERNAME = credentials('github-token')
    }

    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[
                        url: 'https://github.com/OussemaJbeli/boon_frent.git',
                        credentialsId: 'github-token'
                    ]]
                ])
            }
        }

        // Rest of your stages remain unchanged
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
