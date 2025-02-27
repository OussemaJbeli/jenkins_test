pipeline {
    agent any

    environment {
        GIT_USERNAME = credentials('github-token')
    }

    stages {
        stage('Checkout') {
            steps {
<<<<<<< HEAD
                withCredentials([string(credentialsId: 'github-token', variable: 'GITHUB_TOKEN')]) {
                    sh 'git config --global credential.helper store'
                    sh 'git config --global user.name "OussemaJbeli"'
                    sh 'git config --global user.email "jbelioussema33@gmail.com"'
                    sh 'git clone https://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@github.com/OussemaJbeli/boon_frent.git'
                }
=======
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[
                        url: 'https://github.com/OussemaJbeli/boon_frent.git',
                        credentialsId: 'github-token'
                    ]]
                ])
>>>>>>> df3752c60d133c784bd1e291c4a8757766b707e5
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
