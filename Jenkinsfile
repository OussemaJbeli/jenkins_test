pipeline {
    agent any

    environment {
        GIT_USERNAME = credentials('github-token')
    }

    stages {
        stage('Checkout') {
            steps {
                withCredentials([string(credentialsId: 'github-token', variable: 'GITHUB_TOKEN')]) {
                    sh 'git config --global credential.helper store'
                    sh 'git config --global user.name "OussemaJbeli"'
                    sh 'git config --global user.email "jbelioussema33@gmail.com"'
                    sh 'git clone https://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@github.com/OussemaJbeli/boon_frent.git'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
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
