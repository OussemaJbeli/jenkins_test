pipeline {
    agent any

    environment {
        GIT_USERNAME = credentials('github-token')
    }

    stages {
        stage('Checkout') {
            steps {
                bat 'git config --global user.name "OussemaJbeli"'
                bat 'git config --global user.email "jbelioussema33@gmail.com"'
                bat '''
                    git clone https://%GIT_USERNAME%@github.com/OussemaJbeli/boon_frent.git
                '''
            }
        }

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
