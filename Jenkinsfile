pipeline {
    agent any
    environment { GIT_USERNAME = credentials('github-token') }
    stages {
        stage('Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[ url: 'https://github.com/OussemaJbeli/boon_frent.git', credentialsId: 'github-token' ]]
                ])
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
        stage('Checkout Selenium Tests') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[ url: 'https://github.com/OussemaJbeli/py_unit_test.git', credentialsId: 'github-token' ]]
                ])
            }
        }
        stage('Test with Selenium') {
            steps {
                bat 'pip install -r requirements.txt' // Install dependencies
                bat 'python test.py' // Run Selenium test script
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
