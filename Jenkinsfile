pipeline {
    agent any

    environment {
        GIT_USERNAME = credentials('github-token')
    }

    stages {
        stage('Checkout') {
            steps {
                withCredentials([string(credentialsId: 'github-token', variable: 'GITHUB_TOKEN')]) {
                    powershell 'git config --global credential.helper store'
                    powershell 'git config --global user.name "OussemaJbeli"'
                    powershell 'git config --global user.email "jbelioussema33@gmail.com"'
                    powershell "git clone https://${GIT_USERNAME}@github.com/OussemaJbeli/boon_frent.git"
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                powershell 'npm install'
            }
        }

        stage('Build') {
            steps {
                powershell 'npm run build'
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
